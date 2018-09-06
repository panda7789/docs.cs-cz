---
title: Změna deklarace Namespace v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6b80a885f43facf4b3d4dd1dcb56d937d4f8de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878467"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Změna deklarace Namespace v dokumentu XML
**XmlDocument** vystavuje deklarace oboru názvů a **xmlns** atributy jako součást modelu objektu dokumentu. Tyto jsou uložené v **XmlDocument**, takže při ukládání dokumentu, můžete zachovat umístění těchto atributů. Změna těchto atributů nemá žádný vliv na **název**, **NamespaceURI**, a **předpony** vlastnosti ostatní uzly již ve stromové struktuře. Například pokud načítáte následující dokument pak bude `test` element má **NamespaceURI** `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Pokud odeberete `xmlns` atribut následujícím způsobem, pak bude `test` element má stále **NamespaceURI** z `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobně pokud chcete přidat jiný `xmlns` atribut `doc` element následujícím způsobem, pak bude `test` element má stále **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Proto se mění `xmlns` atributy se nemají žádný vliv, dokud uložit a znovu načíst **XmlDocument** objektu.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
