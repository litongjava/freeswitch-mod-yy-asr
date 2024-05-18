

## build
```
gcc -shared -fPIC -o /usr/local/freeswitch/mod/mod_yyasr.so mod_yyasr.c -I /usr/local/freeswitch/include/freeswitch
```

```
cp conf/yyasr.conf.xml /usr/local/freeswitch/conf/autoload_configs/
```

```
vi /usr/local/freeswitch/conf/autoload_configs/modules.conf.xml
```


```
<!-- yyasr asr module testing -->
<extension name="yyasr_demo">
  <condition field="destination_number" expression="^9887$">
    <action application="answer"/>
    <action application="sleep" data="2000"/>
    <action application="get_user_id"/>
    <action application="lua" data="yyasr_demo.lua"/>
  </condition>
</extension>
```