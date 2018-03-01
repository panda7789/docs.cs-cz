---
title: '&lt;appSettings&gt; element pro &lt;konfigurace&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cebb9ba7ebeb483233276324289a4ddc5a0bc381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > elementu pro \<konfigurace >

Obsahuje vlastní nastavení aplikace. Toto je předdefinovaný konfigurační oddíl poskytované rozhraní .NET Framework.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **soubor**  | Nepovinný atribut.<br><br>Určuje relativní cestu k externí soubor obsahující nastavení konfigurace vlastní aplikace. Zadaný soubor obsahuje stejný druh nastavení, které jsou určené v  **\<Přidat >**,  **\<odebrat >**, a  **\<clear >** elementy a používá stejný dvojice klíč/hodnota formátovat jako těchto elementů.<br><br>Zadaná cesta je relativní vzhledem ke hlavní konfiguračního souboru. Aplikaci Windows Forms, to je binární složky (například */bin/ladění*), ne však umístění konfiguračního souboru aplikace. Pro aplikace webových formulářů, cesta je relativní vůči kořenovému adresáři aplikace, kde *web.config* se nachází soubor.<br><br>Všimněte si, že modul runtime ignoruje atribut, pokud zadaný soubor nelze nalézt. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<Konfigurace >** – Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Přidá vlastní nastavení aplikace. |
| [**\<Clear >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Vymaže všechna nastavení dříve definovaném aplikace. |
| [**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Odebere nastavení dříve definovaném aplikace. |

## <a name="remarks"></a>Poznámky

 **\<AppSettings >** element ukládá informace o konfiguraci vlastní aplikaci, například databázové připojovací řetězce, cesty k souborům, adresy URL XML webových služeb nebo jiných vlastní konfigurační informace pro aplikace. Páry klíč – hodnota zadaná v  **\<appSettings >** element probíhal v kódu pomocí <xref:System.Configuration.ConfigurationSettings> – třída.

Můžete použít **soubor** atribut  **\<appSettings >** element *Web.config* a konfigurační soubory aplikace. Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepíše nastavení zadaná  **\<appSettings >** element. **Souboru** atribut lze použít v týmu vývoj scénářích správy zdrojového kódu, například když uživatel chce pro přepsání nastavení projektu zadané v konfiguračním souboru aplikace.

Konfigurační soubory určeného **soubor** kořenový uzel musí mít atribut  **\<appSettings >** místo  **\<konfigurace >**.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor s nastavením externí aplikaci (*custom.config*), který definuje vlastní nastavení aplikace:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Následující příklad ukazuje konfigurační soubor aplikace, která načítá nastavení v souboru externích nastavení a nastaví vlastní nastavení aplikace:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
