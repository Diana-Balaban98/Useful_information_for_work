[Публикация приложения на GitHub Pages](https://reactgo.com/deploy-react-app-github-pages/)

### 1. Открываем в проекте файл package.json
### 2. Вставляем в объект ключ с именем homepage, значением ключа является ссылка на задеплоенный проект на GithubPage
```js
"homepage":"https://yourusername.github.io/repository-name"
```
- yourusername - свое имя, которым подписаны в Github
- repository-name - название репозитория, в котором лежит проект

### 3. Ставим в проект библиотеку gh-pages

команда через npm: 
```js
npm install --save gh-pages
```

команда через yarn: 
```js
yarn add gh-pages
```

### 4. Проверяем, что библиотека установилась. Заходим в файл package.json и смотрим в объект "dependencies"
```js
"dependencies": {
"gh-pages": "^5.0.0",
},
```

### 5. Также в файле package.json в объект "scripts" добавляем 2 команды, если их нет (обычно стоят по умолчанию):
```js
"scripts":{
"predeploy": "npm run build",
"deploy": "gh-pages -d build",
}
```

### 6. В консоли WebStorm запускаем команду:
если на npm: 
```js
npm run deploy
```
если на yarn: 
```js
yarn run deploy
```

### 7. Пока проект билдится в папке проекта появится папка build

### 8. Если проект успешно сбилдился в консоли появится отметка: Published и Done in (время в секундах)

### 9. Заходим на GitHub репозиторий проекта и обновляем страницу

### 10. Видим в репозитории проекта, что создались 2 ветки (2 branches), кликаем по ним

### 11. Проверяем, что в навигации Overview есть 3 поля (Default branch, Your branches, Active branches)

### 12. Кликаем по ссылке gh-pages в поле Your branches или в поле Active branches

### 13. Справа страницы есть поле Environments 1  github-pages Active (нарисована ракета) - кликаем по ссылке github-pages

### 14. Перейдя по ссылке нас перенаправляют на новую страницу Deployments / History - справа видим кнопку View deployment

### 15. Кликаем на кнопку и переходим на задеплоенный проект. Поздавялю! Надеюсь, все получилось :) 
