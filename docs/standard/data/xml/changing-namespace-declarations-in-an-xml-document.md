---
title: Změna deklarací oboru názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5457eab1f34eb3e7424d508509f5dd6a42ffb51f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976937"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Změna deklarací oboru názvů v dokumentu XML
**XmlDocument** zpřístupňuje deklarace oboru názvů a atributy **xmlns** jako součást modelu objektu dokumentu. Ty jsou uloženy v dokumentu **XmlDocument**, takže když dokument uložíte, může zachovat umístění těchto atributů. Změna těchto atributů nemá žádný vliv na vlastnosti **Name**, **NamespaceURI**a **prefixu** dalších uzlů, které jsou již ve stromové struktuře. Například pokud načtete následující dokument, `test` element má **NamespaceURI** `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Odeberete-li atribut `xmlns` následujícím způsobem, má `test` prvek stále **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobně platí, že pokud přidáte jiný atribut `xmlns` do prvku `doc` následujícím způsobem, `test` element má nadále `123`**NamespaceURI** .  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Proto změna atributů `xmlns` nebude mít žádný vliv, dokud neuložíte a znovu načtete objekt **XmlDocument** .  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
