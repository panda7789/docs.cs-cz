---
title: Me, My, MyBase a MyClass
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
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400846"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase a MyClass v jazyce Visual Basic
`Me`, `My` `MyBase`, `MyClass` a v jazyce Visual Basic mají podobné názvy, ale různé účely. Toto téma popisuje každou z těchto entit za účelem jejich rozlišení.  
  
## <a name="me"></a>Já  
 Klíčové `Me` slovo poskytuje způsob, jak odkazovat na konkrétní instanci třídy nebo struktury, ve kterém je aktuálně spuštěn kód. `Me`chová se jako proměnná objektu nebo proměnná struktury odkazující na aktuální instanci. Použití `Me` je zvláště užitečné pro předávání informací o aktuálně spuštěné instanci třídy nebo struktury do procedury v jiné třídě, struktuře nebo modulu.  
  
 Předpokládejme například, že máte následující postup v modulu.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Tento postup můžete volat a předat <xref:System.Windows.Forms.Form> aktuální instanci třídy jako argument pomocí následujícího příkazu.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 Tato `My` funkce poskytuje snadný a intuitivní přístup k řadě tříd rozhraní .NET Framework, což umožňuje uživateli jazyka Visual Basic pracovat s počítačem, aplikací, nastavením, prostředky a tak dále.  
  
## <a name="mybase"></a>MyBase  
 Klíčové `MyBase` slovo se chová jako proměnná objektu odkazující na základní třídu aktuální instance třídy. `MyBase`Se běžně používá pro přístup k členům základní třídy, které jsou přepsány nebo stínovány v odvozené třídě. `MyBase.New`se používá k explicitnímu volání konstruktoru základní třídy z konstruktoru odvozené třídy.  
  
## <a name="myclass"></a>Myclass  
 Klíčové `MyClass` slovo se chová jako proměnná objektu odkazující na aktuální instanci třídy, jak bylo původně implementováno. `MyClass`je podobná `Me`, ale všechny volání metod na něm `NotOverridable`jsou považovány, jako by metoda byla .  
  
## <a name="see-also"></a>Viz také

- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
