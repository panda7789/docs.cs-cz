---
title: Změna deklarací oboru názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: e55486feeb427c95a9394ac83758e6052603921e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291575"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Změna deklarací oboru názvů v dokumentu XML
**XmlDocument** zpřístupňuje deklarace oboru názvů a atributy **xmlns** jako součást modelu objektu dokumentu. Ty jsou uloženy v dokumentu **XmlDocument**, takže když dokument uložíte, může zachovat umístění těchto atributů. Změna těchto atributů nemá žádný vliv na vlastnosti **Name**, **NamespaceURI**a **prefixu** dalších uzlů, které jsou již ve stromové struktuře. Například pokud načtete následující dokument, pak `test` element má **NamespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Pokud atribut odeberete následujícím `xmlns` způsobem, `test` má element stále **NamespaceURI** `123` .  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobně platí, že pokud přidáte jiný `xmlns` atribut `doc` prvku následujícím způsobem, pak `test` má element stále **NamespaceURI** `123` .  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Proto Změna `xmlns` atributů nebude mít žádný vliv, dokud neuložíte a znovu načtete objekt **XmlDocument** .  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
