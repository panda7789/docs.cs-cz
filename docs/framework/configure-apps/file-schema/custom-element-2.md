---
title: "Vlastní element NameValueSectionHandler a DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2154e2a178050e5bafa7d19f37a766141d0a5838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Vlastní element NameValueSectionHandler a DictionarySectionHandler

Definuje nastavení pro vlastní konfiguračních oddílů, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<sectionName >**

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<Přidat >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler>  | Přidá nastavení vlastní aplikace. |
| [**\<Odebrat >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler> |    Odebere dříve definovaném nastavení. |
| [**\<Clear >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler> | Vymaže všechny dříve definované nastavení v oddílu. |

## <a name="remarks"></a>Poznámky

 **\<SectionName >** element je vlastní definované  **\<části >** značky v  **\<configSections >**elementu.

Následující tabulka uvádí, že typ objektu ConfigurationSettings.GetConfig metoda vrátí pro každou obslužnou rutinu konfiguračního oddílu:

| Obslužná rutina konfiguračního oddílu                        | Návratový typ                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat oddíly, které chcete použít <xref:System.Configuration.DictionarySectionHandler> a <xref:System.Configuration.NameValueSectionHandler> třídy. 

První vlastní element je  **\<dictionarySample >**, který obsahuje nastavení číst <xref:System.Configuration.DictionarySectionHandler> třídy v `System.dll` sestavení. Druhý vlastní element je  **\<mySection >**, který obsahuje nastavení číst <xref:System.Configuration.NameValueSectionHandler> třídy v `System.dll` sestavení.

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

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
