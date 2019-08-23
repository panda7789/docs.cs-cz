---
title: <appSettings> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: a64db49b521651ccff8b928720fe3273f8600b68
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921328"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > element pro \<konfigurační >

Obsahuje vlastní nastavení aplikace. Toto je předdefinovaný konfigurační oddíl poskytnutý .NET Framework.

[ **\<> Konfigurace**](../configuration-element.md)   
&nbsp;&nbsp; **\<appSettings>**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **souborů**  | Nepovinný atribut.<br><br>Určuje relativní cestu k externímu souboru, který obsahuje vlastní nastavení konfigurace aplikace. Zadaný soubor obsahuje stejný druh nastavení, které jsou zadány v  **\<> Přidat**,  **\<odebrat >** a  **\<vymazat >** prvky a jako tyto prvky používá stejný formát dvojice klíč/hodnota.<br><br>Zadaná cesta je relativní vzhledem k hlavnímu konfiguračnímu souboru. V případě aplikace model Windows Forms se jedná o binární složku (například */bin/Debug*), nikoli o umístění konfiguračního souboru aplikace. Pro aplikace webových formulářů je cesta relativní k kořenovému adresáři aplikace, kde je umístěn soubor *Web. config* .<br><br>Všimněte si, že modul runtime ignoruje atribut, pokud zadaný soubor nelze nalézt. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [Element  **>\<konfigurace**](../configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [ **\<add>** ](add-element-for-appsettings.md) | Přidá vlastní nastavení aplikace. |
| [ **\<Vymazat >** ](clear-element-for-appsettings.md) | Vymaže všechna dříve definovaná nastavení aplikace. |
| [ **\<remove>** ](remove-element-for-appsettings.md) | Odebere dříve definované nastavení aplikace. |

## <a name="remarks"></a>Poznámky

Element **appSettings > ukládá vlastní informace o konfiguraci aplikace, například připojovací řetězce k databázi, cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci. \<** Páry klíč/hodnota zadané v <xref:System.Configuration.ConfigurationSettings>  **\<elementu appSettings >** jsou k dispozici v kódu pomocí třídy.

Můžete použít atribut **File** v  **\<elementu appSettings >** souboru *Web. config* a konfiguračních souborů aplikace. Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepisuje nastavení zadané v  **\<elementu appSettings >** . Atribut **File** lze použít ve scénářích vývoje týmu správy zdrojového kódu, například když chce uživatel přepsat nastavení projektu zadané v konfiguračním souboru aplikace.

Konfigurační soubory určené atributem **souboru** musí mít kořenový uzel  **\<appSettings >** spíše než  **\<konfigurační >** .

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení externí aplikace (*Custom. config*), který definuje vlastní nastavení aplikace:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastavuje vlastní nastavení aplikace:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](../index.md)
