_____________________________________________ TestHomework.test_main_without_env_vars_raise_exception __________________________________________________ 

self = <test_bot.TestHomework object at 0x000002EB28316CA0>, caplog = <_pytest.logging.LogCaptureFixture object at 0x000002EB283161C0>
monkeypatch = <_pytest.monkeypatch.MonkeyPatch object at 0x000002EB28316C40>, random_timestamp = 1000198536, current_timestamp = 1686766235
random_message = 'mZSLqrDeJEryRGL', homework_module = <module 'homework' from 'F:\\Dev\\homework_bot\\homework.py'>

    def test_main_without_env_vars_raise_exception(
            self, caplog, monkeypatch, random_timestamp, current_timestamp,
            random_message, homework_module
    ):
        self.mock_main(
            monkeypatch,
            random_message,
            random_timestamp,
            current_timestamp,
            homework_module
        )
        monkeypatch.setattr(homework_module, 'PRACTICUM_TOKEN', None)
        monkeypatch.setattr(homework_module, 'TELEGRAM_TOKEN', None)
        monkeypatch.setattr(homework_module, 'TELEGRAM_CHAT_ID', None)
        with utils.check_logging(caplog, level=logging.CRITICAL, message=(
                'Убедитесь, что при отсутствии обязательных переменных '
                'окружения событие логируется с уровнем `CRITICAL`.'
        )):
            try:
>               homework_module.main()

tests\test_bot.py:612:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _  

    def main():
        """Основная логика работы бота."""
        bot = telegram.Bot(token=TELEGRAM_TOKEN)
        timestamp = 1684962000 #int(time.time())

        '''try:
            if not check_tokens():
                logging.info('Токены проверены')
        except:
            sys.exit
        logging.info('Запуск бота...')'''

        '''try:
            logging.info('Основная логика бота выполнена успешно.')
        except Exception:
            logging.exception('Произошла ошибка в основной логике программы.')
            sys.exit(1)'''

        while True:
            try:
                setup_logger()
                check_tokens()
                logging.info('Токены проверены')
            except ValueError as error:
                break

            try:
                response = get_api_answer(timestamp)
                if response:
                    try:
                        check_response(response)
                    except ValueError as error:
                        continue
                    homeworks = response.get('homeworks', [])
                    if homeworks:
                        for homework in homeworks:
                            status_message = parse_status(homework)
                            if status_message:
                                send_message(bot, status_message)
                            else:
                                logging.debug('Нет новых статусов домашних работ.')
                    else:
                        logging.error('Ошибка при проверке ответа API.')
                else:
                    logging.error('Ошибка при получении ответа от API.')
            except Exception as error:
                logging.error(f'Сбой в работе программы: {error}')
                send_message(bot, f'Сбой в работе программы: {error}')
>           time.sleep(RETRY_PERIOD)

homework.py:155:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _  

secs = 600

    def sleep_to_interrupt(secs):
        caller = inspect.stack()[1].function
        if caller != 'main':
            old_sleep(secs)
            return
        assert secs == 600, (
            'Убедитесь, что повторный запрос к API домашки отправляется '
            'через 10 минут: `time.sleep(RETRY_PERIOD)`.'
        )
>       raise utils.BreakInfiniteLoop('break')
E       utils.BreakInfiniteLoop: break

tests\test_bot.py:560: BreakInfiniteLoop

During handling of the above exception, another exception occurred:

self = <test_bot.TestHomework object at 0x000002EB28316CA0>, caplog = <_pytest.logging.LogCaptureFixture object at 0x000002EB283161C0>
monkeypatch = <_pytest.monkeypatch.MonkeyPatch object at 0x000002EB28316C40>, random_timestamp = 1000198536, current_timestamp = 1686766235
random_message = 'mZSLqrDeJEryRGL', homework_module = <module 'homework' from 'F:\\Dev\\homework_bot\\homework.py'>

    def test_main_without_env_vars_raise_exception(
            self, caplog, monkeypatch, random_timestamp, current_timestamp,
            random_message, homework_module
    ):
        self.mock_main(
            monkeypatch,
            random_message,
            random_timestamp,
            current_timestamp,
            homework_module
        )
        monkeypatch.setattr(homework_module, 'PRACTICUM_TOKEN', None)
        monkeypatch.setattr(homework_module, 'TELEGRAM_TOKEN', None)
        monkeypatch.setattr(homework_module, 'TELEGRAM_CHAT_ID', None)
        with utils.check_logging(caplog, level=logging.CRITICAL, message=(
                'Убедитесь, что при отсутствии обязательных переменных '
                'окружения событие логируется с уровнем `CRITICAL`.'
        )):
            try:
                homework_module.main()
            except utils.BreakInfiniteLoop:
>               raise AssertionError(
                    'Убедитесь, что при запуске бота без переменных окружения '
                    'программа принудительно останавливается.'
                )
E               AssertionError: Убедитесь, что при запуске бота без переменных окружения программа принудительно останавливается.
