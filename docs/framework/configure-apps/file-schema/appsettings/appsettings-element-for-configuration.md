---
title: '&lt;appSettings&gt; – element pro &lt;konfigurace&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 0ba57f51d3b1e78239677317933507ff009db035
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190928"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > – element pro \<configuration >

Obsahuje vlastní nastavení aplikace. Toto je předdefinovaný konfigurační oddíl poskytuje rozhraní .NET Framework.

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
| **Soubor**  | Nepovinný atribut.<br><br>Určuje relativní cestu na externí soubor, který obsahuje vlastní nastavení konfigurace aplikace. Zadaný soubor obsahuje stejný druh nastavení, které jsou určené v  **\<Přidat >**,  **\<odebrat >**, a  **\<vymazat >** prvků a používá tyto prvky formátování stejného páru klíč/hodnota.<br><br>Zadaná cesta je relativní vzhledem k hlavní konfigurační soubor. Pro aplikace Windows Forms, je to binární složka (například */bin/debug*), ne však umístění konfiguračního souboru aplikace. Pro aplikace webových formulářů, cesta je relativní vzhledem k kořenový adresář aplikace, kde *web.config* se nachází soubor.<br><br>Všimněte si, že modul runtime ignorovat atribut, pokud zadaný soubor nebyl nalezen. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<Konfigurace >** – Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Přidá nastavení vlastní aplikace. |
| [**\<Vymazat >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Vymaže všechny dříve definované aplikaci nastavení. |
| [**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Odebere nastavení dříve definované aplikace. |

## <a name="remarks"></a>Poznámky

**\<AppSettings >** element ukládá informace o konfiguraci vlastních aplikací, jako jsou databázové připojovací řetězce, cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikace. Páry klíč/hodnota zadaná v  **\<appSettings >** element jsou přístupné z kódu pomocí <xref:System.Configuration.ConfigurationSettings> třídy.

Můžete použít **souboru** atribut  **\<appSettings >** elementu *Web.config* a konfiguračních souborů aplikace. Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepíše nastavení zadaná  **\<appSettings >** elementu. **Souboru** atribut lze použít v týmu vývoje scénářích správy zdrojového kódu, jako je například, pokud uživatel požaduje přepsat nastavení projektu zadané v konfiguračním souboru aplikace.

Konfigurační soubory, které jsou určené **souboru** atribut musí mít kořenový uzel  **\<appSettings >** spíše než  **\<konfigurace >**.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení externí aplikace (*custom.config*), který definuje vlastní nastavení aplikace:

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

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
