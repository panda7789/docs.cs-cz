---
title: Změna deklarací oboru názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: b8aa670764deb8e77cfb67fd16dbcf8b1cc9b4c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711126"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Změna deklarací oboru názvů v dokumentu XML
**XmlDocument** zpřístupňuje deklarace oboru názvů a atributy **xmlns** jako součást modelu objektu dokumentu. Ty jsou uloženy v dokumentu **XmlDocument**, takže když dokument uložíte, může zachovat umístění těchto atributů. Změna těchto atributů nemá žádný vliv na vlastnosti **Name**, **NamespaceURI**a **prefixu** dalších uzlů, které jsou již ve stromové struktuře. Například pokud načtete následující dokument, pak `test` element má **NamespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Pokud `xmlns` atribut odeberete následujícím způsobem, má `test` element stále **NamespaceURI** . `123`  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobně platí, že pokud `xmlns` přidáte jiný atribut `doc` prvku následujícím způsobem, pak má `test` element stále **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Proto Změna `xmlns` atributů nebude mít žádný vliv, dokud neuložíte a znovu načtete objekt **XmlDocument** .  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
