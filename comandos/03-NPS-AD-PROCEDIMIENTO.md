# Procedimiento AD DS y NPS usado en la práctica

**Procedimiento de interfaz gráfica; no existe script PowerShell confirmado.**

1. En el dominio `lab.local`, crear o confirmar los grupos `AAA-NIVEL-0`, `AAA-NIVEL-5` y `AAA-NIVEL-10`, con usuarios de prueba asignados a cada grupo.
2. En NPS registrar como clientes RADIUS a R1 (`10.6.93.1`) y SW1 (`10.6.93.2`). La clave compartida configurada en NPS debe coincidir con Cisco; **no se publica**.
3. Crear/habilitar tres Network Policies con condiciones de pertenencia a los grupos respectivos; permitir acceso mediante PAP para la red controlada de laboratorio.
4. Definir `Service-Type = Login` y Cisco Vendor-Specific Attribute `Cisco-AVPair` (VSA 1, String): `shell:priv-lvl=0`, `shell:priv-lvl=5` o `shell:priv-lvl=10` según la política.
5. Habilitar el registro de solicitudes de autenticación y de contabilidad en NPS. La práctica usó los registros ODBC/Legacy en `C:\Windows\System32\LogFiles`, archivo `IN2610`.
6. Validar accesos SSH, eventos de autenticación y Accounting Start/Stop con sus identificadores de sesión.

**Notas:** Se usó PAP únicamente en un entorno docente controlado; no se recomienda trasladar esta configuración a producción sin revisar los controles criptográficos y de transporte. Las políticas deben mantenerse en el orden que asegure el grupo correspondiente. No se adjuntan exportaciones NPS ni comandos de creación automática porque no fueron aportados.
