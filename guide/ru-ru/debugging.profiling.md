# Профилирование

Kohana предлагает очень простой способ для отображения статистики Вашего приложения:

1. Системных вызовов [Kohana]
2. Запросов (Requests)
3. Запросов к [базам данных](Database)
4. Среднего времени выполнения Вашего приложения

## Пример

Вы можете отобразить или собрать текущую статистику [профилировщика](profiler) в любое время:

    <div id="kohana-profiler">
    <?php echo View::factory('profiler/stats') ?>
    </div>

## Что получится

{{profiler/stats}}