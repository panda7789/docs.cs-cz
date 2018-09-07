---
title: '&lt;Přidat&gt; – Element pro &lt;schemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 48deb8684e53f583e3ff4a5407fadd112d45f749
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44082223"
---
# <a name="ltaddgt-element-for-ltschemaimporterextensionsgt"></a>&lt;Přidat&gt; – Element pro &lt;schemaImporterExtensions&gt;
Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework. Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<Konfigurace >  
\<System.XML.Serialization >  
\<schemaImporterExtensions >  
\<add>  
  
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
|**Typ**|Požadováno. Určuje třídu rozšíření schématu k přidání. **Typ** hodnota atributu musí být na jednom řádku a zahrnout plně kvalifikovaného názvu. Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Serialization.XmlSchemaImporter>  
- [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)  
- [\<schemaImporterExtensions > – Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)
