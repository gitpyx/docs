# API

配网 接口 回调函数

配置参数接口

OTA 接口

## interface

```
 typedef enum
 {
     EJ_NOT_SUBSCRIBED      = -13,
     EJ_ALREADY_SUBSCRIBED  = -12,
     EJ_TIMEOUT             = -11,
     EF_UNSUBSCRIPTION_ERROR= -10,
     EJ_SUBSCRIPTION_ERROR  = -9,
     EJ_PUBLISH_ERROR       = -8,
     EJ_NOT_CONNECTED       = -7,
     EJ_CONNECTION_FAILED   = -6,
     EJ_BAD_URL             = -5,
     EJ_CERT_REQUIRED_ERROR = -4,
     EJ_MEMORY_ERROR        = -3,
     EJ_BAD_ARGS            = -2,
     EJ_FAILURE             = -1,
     EJ_SUCCESS             =  0,
 } ej_ret;

```

```
typedef int (*ej_callback_t)(void);
```

```
typedef struct ej_ctx_t* ej_handle_t;
```

## external function

```
ej_ret ej_init_handle(ej_handle_t *handle);
```

```
ej_set_config
```


```
ej_ret ej_detroy_handle(ej_handle_t *handle);
```

```
ej_ret ej_set_channel(uint8_t *mac);
```

```
ej_ret ej_set_connect_callback(ej_callback_t lost_connect_callback, ej_callback_t restore_connect_callback);
```

```
ej_ret ej_set_thread_priority(int priority);
```

```
ej_ret ej_set_thread_stacksize(ej_handle_t *handle, int size);
```

```
ej_ret ej_connect(ej_handle_t *handler);
```

```
ej_ret ej_disconnect(ej_handle_t *handler);
```

```
//ej_ret ej_snd_proprity_msg(uint8_t *payload);
```

//
ej_ret ej_subscribe(uint8_t *topic, ej_callback func);

//
ej_set_network(int status)


set_sdk_log_level()

ej_printf(modue, ...);

// 

## internal function

```
void timer_init(Timer *timer);
```

```
char time_is_expired(Timer *timer);
```

```
void time_countdown(Timer* timer, unsigned int timeout);
```

```
time_left(Timer *timer);
```

```
network_init(Network *n);
```

```
void network_securedinit(Network *n, const char* ca_buf, size_t ca_size);
```

```
network_connect(Network *n, char *addr, int port);
```

```
network_disconnect(Network *n);
```

```
network_write(Network *n, unsigned char *buf, int len, int timeout_ms);
```

```
network_read(Network *n, unsigned char *buf, int len, int timeout_ms);
```

```
network_udp_init(Network *n);
```

```
network_udp_bind(Network *n);
```

```
network_udp_write(Network *n, unsigned char *buf, int len);
```

```
network_udp_read(Network *n, unsigned char *buf, int len);
```

```
network_udp_close(Network *n);
```

```
mutex_init(Mutex *mutex);
```

```
mutex_lock(Mutex *mutex);
```

```
mutex_unlock(Mutex *mutex);
```

```
mutex_deinit(Mutex *mutex);
```

```
semaphore_int(Semaphore *semaphore);
```

```
semaphore_deinit(Semaphore *semaphore);
```

```
semaphore_wait(Semaphore *semaphore, int timeout);
```

```
semaphore_post(Semaphore *semaphore);
```

```
int thread_create(thread_t *thread, init priority, const char *name, void (*founc)(void *), int stack_size, void *arg);
```

```
int thread_join(thread_t *thread, int timeout);
```

```
int thread_destroy(thread_t *thread);
```

```
int sleep(int ms);
```

```
void *plat_malloc(int size);
```

```
void plat_free(void *mem); 
```

```
uart_open(UART_ID uart_id, uint32_t baudrate)
```

```
uart_close(UART_ID uart_id);
```

```
int16_t uart_read(const uint8_t *buf, uint32_t len);
```

```
int16_t uart_write(uint8_t *buf, uint32_t len);
```

```
int plat_printf(const char *fmt, ...);
```
