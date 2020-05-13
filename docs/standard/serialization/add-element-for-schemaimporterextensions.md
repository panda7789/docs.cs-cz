---
title: Element <add> pro <schemaImporterExtensions>
description: <add>Element přidá typy používané třídou XmlSchemaImporter pro mapování typů XSD na .NET Framework typy.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378470"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<Přidat> element pro \<> schemaImporterExtensions
Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework. Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<> konfigurace  
\<System. XML. Serialization –>  
\<schemaImporterExtensions>  
\<Přidat>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Jméno**|Jednoduchý název, který je použit k vyhledání instance.|  
|**textový**|Povinná hodnota. Určuje třídu rozšíření schématu k přidání. Hodnota atributu **Type** musí být na jednom řádku a musí obsahovat plně kvalifikovaný název typu. Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu přidá typ rozšíření, která XmlSchemaImporter můžete použít, když mapování typů.  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [\<System. XML. Serialization – element>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [\<schemaImporterExtensions – element>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
