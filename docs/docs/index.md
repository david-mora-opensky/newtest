# Documentación de biblioteca

Texto y enlace de prueba [openskyinformation.com](https://www.openskyinformation.com).

## Requerimientos

* Clona el siguiente repositorio [GitHub Repository](https://github.com/david-mora-opensky/read-the-doc-test.git)

## Clase de usuario

```python
class Login(FormView):
    template_name = 'login.html'
    form_class = FormularioLogin
    success_url = reverse_lazy('index')

    @method_decorator(csrf_protect)
    @method_decorator(never_cache)
    def dispatch(self, request, *args, **kwargs):
        if request.user.is_authenticated:
            return HttpResponseRedirect(self.get_success_url())
        else:
            return super(Login, self).dispatch(request, *args, **kwargs)

    def form_valid(self, form):
        login(self.request, form.get_user())
        return super(Login, self).form_valid(form)
```
