---
title: <add> of <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e65b66170465a8b3bb60754feebb7730b959d9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089715"
---
# <a name="add-of-namespacetable"></a>\<Přidat > z \<namespaceTable >
Představuje prvek konfigurace, který obsahuje obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.  
  
 \<system.serviceModel>  
\<směrování >  
\<namespaceTable>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– obor názvů|Řetězec obsahující obor názvů.|  
|Předpona|Řetězec obsahující předponu pro tento obor názvů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namespaceTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
