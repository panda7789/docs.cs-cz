---
title: Me, My, MyBase a MyClass v jazyce Visual Basic
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: f3db5f8f6688e68992f683ac1b1465078aa41231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase a MyClass v jazyce Visual Basic
`Me`, `My`, `MyBase`, a `MyClass` v jazyce Visual Basic mají podobné názvy, ale jiné účely. Toto téma popisuje každou z těchto položek, aby bylo možné odlišit.  
  
## <a name="me"></a>Mně  
 `Me` – Klíčové slovo poskytuje způsob, jak odkazovat na konkrétní instanci třídu nebo strukturu, ve kterém je aktuálně provádění kódu. `Me` chová jako objektová proměnná nebo proměnná struktura odkaz na aktuální instanci. Pomocí `Me` je zvláště užitečná pro předávání informací o aktuálně spuštěném instanci třídu nebo strukturu proceduře v jiné třídy, struktury nebo modul.  
  
 Předpokládejme například, že máte následující postup v modulu.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Můžete tento postup a předejte aktuální instancí třídy <xref:System.Windows.Forms.Form> třída jako argument pomocí následujícího příkazu.  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 `My` Funkce poskytuje snadný a intuitivní přístup k několika [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy, povolení jazyka Visual Basic uživatelům interakci s počítači, aplikace, nastavení, prostředky a tak dále.  
  
## <a name="mybase"></a>MyBase  
 `MyBase` – Klíčové slovo chová jako proměnná objektu odkazuje na základní třídu aktuální instance třídy. `MyBase` se běžně používá pro přístup k členy základní třídy, které jsou přepsat nebo Stínovaný v odvozené třídě. `MyBase.New` slouží k explicitně volání konstruktoru základní třídy z konstruktoru odvozené třídy.  
  
## <a name="myclass"></a>MyClass  
 `MyClass` – Klíčové slovo chová jako odkaz na aktuální instanci třídy jako poprvé implementované proměnné objektu. `MyClass` je podobná `Me`, ale všechny volání metod v něm jsou zpracovány jako kdyby metodu `NotOverridable`.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
