### Реализуйте возможность указания ссылок на страницы книги в различных интернет-магазинах.

В файле models.py была создана модель Link:

```
class Link(models.Model):
    book_a = models.ForeignKey('Book', on_delete=models.CASCADE, null=True)
    link = models.CharField('Ссылка', max_length=255)

    def __str__(self):
        return self.link

    class Meta:
        ordering = ('link',)
        verbose_name = 'Ссылка'
        verbose_name_plural = 'Ссылки'
```

Далее для отображения полей для ввода ссылок в линию был добавлен класс LinkInLine:

```
class LinkInline(admin.TabularInline):
    model = Link
```
Регистрация модели в панели администратора:
```
@admin.register(Link)
class LinkAdmin(admin.ModelAdmin):
    list_display = ('link',)
```
