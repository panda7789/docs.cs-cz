---
title: Podpora Namespace v modelu DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3145df6517df9db580bfcc5d67edd9d1a61f290b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-support-in-the-dom"></a>Podpora Namespace v modelu DOM
XML modelu DOM (Document Object) je zcela clustery pro obor názvů. Jsou podporovány pouze deklaracemi obor názvů XML dokumenty. World Wide Web Consortium (W3C) určuje, že může být jiný obor názvů s deklaracemi DOM aplikace, které implementují úrovně 1 a DOM Level 2 funkce jsou clustery pro obor názvů. Všechny funkce v modelu DOM XML jsou však obor názvů deklaracemi bez ohledu na to, pokud je metoda z úrovně 1 nebo úrovně 2 DOM doporučení.  
  
 Například v nastavení jiný obor názvů s deklaracemi, volání `setAttribute("A:b", "123")`, jak je uvedeno v modelu DOM úrovně 1 doporučení, nevede atribut s předponou `A` a pro místní název `b`. Výsledkem by atributu s hodnotou `A:b`.  
  
 V prostředí využívající technologii obor názvů, volání DOM Level 2 `setAttribute("A:b", "123")` výsledků v atributu s předponou `A` a pro místní název `b`. Toto je, jak rozhraní Microsoft .NET Framework DOM funguje.  
  
 Pro všechny metody, která přebírají parametr name, je proto tyto metody také mít předponu pro kvalifikaci název. Parametr name, jako `A:b` v **setAttribute** metoda DOM úrovně 1, je analyzována následujícím způsobem:  
  
-   Pokud neexistují žádné dvojtečky (:), pak je nastavit místní název `name` parametr a předponu a NamespaceURI jsou prázdné řetězce.  
  
-   Pokud se najde dvojtečkou název rozdělit na dvě části na základě pozice prvního znaku dvojtečkou. Předpona, která je nastavena na nalezen před dvojtečkou řetězec a místní název je nastaven na řetězec nalezen po dvojtečkou. Pro metody, které nepřebírají hodnotu NamespaceURI NamespaceURI není vyřešený a zůstane nastavit na prázdný řetězec. NamespaceURI, jinak hodnota nastavena na řetězec předaný metodě. Pokud předponu není definován, pak se **Uložit** metoda a **InnerXml** a **OuterXml** vlastnosti služeb při selhání.  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
