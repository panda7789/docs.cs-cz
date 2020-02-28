---
title: <add> – element pro <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 4f47623aa305ae6e98625acc3d199a76e27d2ea5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159933"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<přidat > element pro \<schemaImporterExtensions >
Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework. Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 Konfigurace \<>  
\<System. XML. Serialization >  
\<schemaImporterExtensions >  
\<přidat >  
  
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
|**type**|Povinná hodnota. Určuje třídu rozšíření schématu k přidání. Hodnota atributu **Type** musí být na jednom řádku a musí obsahovat plně kvalifikovaný název typu. Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<schemaImporterExtensions >|Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
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
- [\<element System. XML. Serialization > elementu](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [\<element > schemaImporterExtensions](../../../docs/standard/serialization/schemaimporterextensions-element.md)
