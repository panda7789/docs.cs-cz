---
title: Vlastní element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215481"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Vlastní element pro NameValueSectionHandler a DictionarySectionHandler

Definuje nastavení pro vlastní konfigurační oddíly, které používají <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> třídy a.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Description |
| --- | ----------- |
| [**\<add>**](add-element-for-custom-2.md)pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler>  | Přidá vlastní nastavení aplikace. |
| [**\<remove>**](remove-element-for-custom-2.md)pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler> | Odebere dříve definované nastavení. |
| [**\<clear>**](clear-element-for-custom-2.md)pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler> | Vymaže všechna dříve definovaná nastavení v oddílu. |

## <a name="remarks"></a>Poznámky

**\<sectionName>** Element je vlastní element definovaný **\<section>** tagem v **\<configSections>** elementu.

V následující tabulce je uveden typ objektu, který metoda ConfigurationSettings. GetConfig vrátí pro každou obslužnou rutinu konfiguračního oddílu:

| Obslužná rutina konfiguračního oddílu                        | Návratový typ                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat oddíly, které používají <xref:System.Configuration.DictionarySectionHandler> třídy a <xref:System.Configuration.NameValueSectionHandler> .

První vlastní prvek je **\<dictionarySample>** , který obsahuje nastavení čtená <xref:System.Configuration.DictionarySectionHandler> třídou v `System.dll` sestavení. Druhý vlastní prvek je **\<mySection>** , který obsahuje nastavení čtená <xref:System.Configuration.NameValueSectionHandler> třídou v `System.dll` sestavení.

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
