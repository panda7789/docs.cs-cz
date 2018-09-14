---
title: Podpora Namespace v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bcc796f8d895e3daa81a9607bd7c4941b747cf24
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512826"
---
# <a name="namespace-support-in-the-dom"></a>Podpora Namespace v modelu DOM
Je zcela oboru názvů s ohledem na XML Document Object Model (DOM). Jsou podporovány pouze s ohledem na obor názvů XML dokumentů. World Wide Web Consortium (W3C) určuje, že může být mimo obor názvů s deklaracemi modelu DOM aplikace, které implementují úrovně 1 a modelu DOM úrovně 2 funkcí jsou s ohledem na obor názvů. Všechny funkce v modelu DOM jazyka XML jsou však s ohledem na obor názvů bez ohledu na to, pokud je metoda od úrovně 1 nebo úrovně 2 modelu DOM doporučení.  
  
 Například v mimo obor názvů – s ohledem na nastavení, volání `setAttribute("A:b", "123")`, jak je uvedeno v modelu DOM na úrovni 1 doporučení, nemá za následek atribut s předponou `A` a místní název `b`. Výsledkem by byla atributu s hodnotou `A:b`.  
  
 V prostředí s ohledem na obor názvů, volání na úroveň 2 modelu DOM `setAttribute("A:b", "123")` výsledků v atributu s předponou `A` a místní název `b`. Toto je Princip modelu DOM rozhraní Microsoft .NET Framework.  
  
 Pro všechny metody, které přebírají parametr name, je proto tyto metody také mít předponu kvalifikovat název. Parametr name, jako `A:b` v **setAttribute** metoda 1. úrovně modelu DOM, je analyzován následujícím způsobem:  
  
-   Pokud neexistují žádné dvojtečky (:), pak místní název je nastavený `name` parametr a předponu a NamespaceURI jsou prázdné řetězce.  
  
-   Pokud se najde dvojtečkou název rozdělit do dvou částí na základě pozice první znak dvojtečky. Předpona, která je nastavena na řetězec nalezen před dvojtečku a místní název nastavený na řetězec nalezen za dvojtečkou. Pro metody, které nepřebírají hodnotu NamespaceURI jeho atribut NamespaceURI není vyřešený a zůstane nastavit na prázdný řetězec. V opačném případě jeho atribut NamespaceURI nastavený na řetězec předaný metodě. Pokud předpona, která není definován, pak bude **Uložit** metoda a **InnerXml** a **OuterXml** vlastnosti selhání.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
