---
title: "Změna Namespace – deklarace v dokumentu XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6db78e689b8529ef62a3b42c2cefb6a5b3d3f02f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Změna Namespace – deklarace v dokumentu XML
**Třídou XMLDocument nastavenou na** vystavuje deklarace oboru názvů a **xmlns** atributy jako součást modelu objektu dokumentu. Tyto jsou uložené v **třídou XMLDocument nastavenou na**, takže při ukládání dokumentu, ho můžete zachovat umístění těchto atributů. Změna těchto atributů nemá žádný vliv na **název**, **NamespaceURI**, a **předpony** vlastnosti dalších uzlů již ve stromové struktuře. Například, Pokud zavedete v následujících dokumentech pak se `test` má element **NamespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Pokud odeberete `xmlns` atribut následujícím způsobem, pak se `test` element má stále **NamespaceURI** z `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobně pokud přidáte jinou `xmlns` atribut `doc` element následujícím způsobem, pak se `test` element má stále **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Proto změna `xmlns` atributy bude mít žádný účinek, dokud uložíte a znovu načtete **třídou XMLDocument nastavenou na** objektu.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
