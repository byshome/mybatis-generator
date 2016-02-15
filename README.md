# mybatis-generator
个性化修改过的mybatis-generator

java -Djava.ext.dirs=./ -jar mybatis-generator-core-1.3.3.jar -configfile ./rpfqordercenter.xml -overwrite
>支持注释，支持大写分割字段符

##配置文件写法需要注意

> 数据库连接串 jdbc:mysql://192.168.2.200/rpfqordercenter?characterEncoding=utf8&amp;allowMultiQueries=true&amp;**useInformationSchema=true**
> 增加注释的配置 commentGenerator=>需要增加属性 <property name="addRemarkComments" value="true"/>
> 在更新数据库的Mapper方法上增加@MasterDataSource的配置  javaClientGenerator＝》下增加配置<modifyDbAnnotation name="masterDataSource" value="com.u51.rpfqorderservice.datasources.annotations.MasterDataSource"/>
> 增加分表符支持 <table tableName="T_Order_Pay_Record_00" domainObjectName="OrderPayRecord" **tableIndexSuffix="00"*/>
> 主键生成配置 table => <generatedKey column="RecordId" sqlStatement="MySql" identity="true" />
> 在Model中增加字段注解 javaModelGenerator =>下增加配置  <fieldAnnotation name="jsonSerializer" value="com.fasterxml.jackson.databind.annotation.JsonDeserialize(using = JacksonDateDeserializer.class)" importType="com.u51.utils.jackson.JacksonDateDeserializer" targetType="java.util.Date"/>
