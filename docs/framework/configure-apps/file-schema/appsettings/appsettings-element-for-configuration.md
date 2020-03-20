---
title: <appSettings> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155528"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings> \<element pro konfiguraci>

Obsahuje vlastní nastavení aplikace. Toto je předdefinovaná konfigurační část poskytovaná rozhraním .NET Framework.

konfigurace &nbsp; &nbsp;>[** \<**](../configuration-element.md) ** \<aplikaceNastavení>**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **Soubor**  | Nepovinný atribut.<br><br>Určuje relativní cestu k externímu souboru obsahujícímu vlastní nastavení konfigurace aplikace. Zadaný soubor obsahuje stejný druh nastavení, které jsou zadány v ** \<>sčítání **, ** \<odeberte>** a ** \<zrušte>** prvky a používá stejný formát páru klíč/hodnota jako tyto prvky.<br><br>Zadaná cesta je relativní vzhledem k hlavnímu konfiguračnímu souboru. Pro aplikaci Windows Forms se jedná o binární složku (například */bin/debug*), nikoli o umístění konfiguračního souboru aplikace. U aplikací webových formulářů je cesta relativní ke kořenovému adresáři aplikace, kde je umístěn soubor *web.config.*<br><br>Runtime ignoruje atribut, pokud zadaný soubor nelze najít. |

## <a name="parent-element"></a>Nadřazený prvek

|     | Popis |
| --- | ----------- |
| [** \<konfigurační>** Prvek](../configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<přidat>**](add-element-for-appsettings.md) | Přidá vlastní nastavení aplikace. |
| [**\<jasné>**](clear-element-for-appsettings.md) | Vymaže všechna dříve definovaná nastavení aplikace. |
| [**\<odebrat>**](remove-element-for-appsettings.md) | Odebere dříve definované nastavení aplikace. |

## <a name="remarks"></a>Poznámky

Prvek ** \<appSettings>** ukládá vlastní informace o konfiguraci aplikace, jako jsou připojovací řetězce databáze, cesty k souborům, adresy URL webové služby XML nebo jiné vlastní informace o konfiguraci aplikace. Dvojice klíč/hodnota zadané v ** \<appSettings>** element jsou přístupné <xref:System.Configuration.ConfigurationSettings> v kódu pomocí třídy.

Atribut **souboru** můžete použít v ** \<aplikaciNastavení>** prvek konfiguračních souborů *Web.config* a aplikace. Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepíše nastavení zadaná v ** \<elementu>appSettings.** Atribut **souboru** lze použít ve scénářích vývoje týmu správy zdrojového kódu, například když uživatel chce přepsat nastavení projektu zadané v konfiguračním souboru aplikace.

Konfigurační soubory určené atributem **souboru** musí mít kořenový uzel ** \<>nastavení aplikace,** ** \< **nikoli konfigurace>.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení externí aplikace *(custom.config),* který definuje vlastní nastavení aplikace:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastaví vlastní nastavení aplikace:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](../index.md)
