---
title: <appSettings> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: e1f285aae10a89fa49846534d5b47e15920294ea
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452276"
---
# <a name="appsettings-element-for-configuration"></a>\<Element appSettings > pro \<konfigurace >

Obsahuje vlastní nastavení aplikace. Toto je předdefinovaný konfigurační oddíl poskytnutý .NET Framework.

[**konfigurační >\<** ](../configuration-element.md)   
&nbsp;&nbsp; **\<appSettings >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **souborů**  | Nepovinný atribut.<br><br>Určuje relativní cestu k externímu souboru, který obsahuje vlastní nastavení konfigurace aplikace. Zadaný soubor obsahuje stejný druh nastavení, které jsou zadány v **\<přidat >** , **\<odebrat >** a **\<odstranit >** prvky a jako tyto prvky používá stejný formát dvojice klíč/hodnota.<br><br>Zadaná cesta je relativní vzhledem k hlavnímu konfiguračnímu souboru. V případě aplikace model Windows Forms se jedná o binární složku (například */bin/Debug*), nikoli o umístění konfiguračního souboru aplikace. Pro aplikace webových formulářů je cesta relativní k kořenovému adresáři aplikace, kde je umístěn soubor *Web. config* .<br><br>Modul runtime ignoruje atribut, pokud zadaný soubor nelze nalézt. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**konfigurace\<>** Objekt](../configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [ **\<přidat >** ](add-element-for-appsettings.md) | Přidá vlastní nastavení aplikace. |
| [ **\<vymazat >** ](clear-element-for-appsettings.md) | Vymaže všechna dříve definovaná nastavení aplikace. |
| [ **\<odebrat >** ](remove-element-for-appsettings.md) | Odebere dříve definované nastavení aplikace. |

## <a name="remarks"></a>Poznámky

Element **\<appSettings >** ukládá vlastní informace o konfiguraci aplikace, například připojovací řetězce k databázi, cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci. Páry klíč/hodnota zadané v elementu **\<appSettings >** jsou k dispozici v kódu pomocí třídy <xref:System.Configuration.ConfigurationSettings>.

Atribut **File** lze použít v prvku **\<appSettings >** elementu *Web. config* a konfiguračních souborů aplikace. Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepisuje nastavení zadané v prvku **\<appSettings >** . Atribut **File** lze použít ve scénářích vývoje týmu správy zdrojového kódu, například když chce uživatel přepsat nastavení projektu zadané v konfiguračním souboru aplikace.

Konfigurační soubory určené atributem **souboru** musí mít kořenový uzel **\<appSettings >** spíše než **\<> Konfigurace**.

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

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](../index.md)
