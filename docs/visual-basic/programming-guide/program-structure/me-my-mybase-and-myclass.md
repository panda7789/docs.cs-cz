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
ms.openlocfilehash: a8df6e48fd5bce9bb28d8aef7e031f36741ad0ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813389"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase a MyClass v jazyce Visual Basic
`Me`, `My`, `MyBase`, a `MyClass` v jazyce Visual Basic mají podobné názvy, ale různým účelům. Toto téma popisuje všechny tyto entity, aby bylo možné odlišit.  
  
## <a name="me"></a>Mně  
 `Me` – Klíčové slovo poskytuje způsob, jak odkazovat na konkrétní instanci třídy nebo struktury, ve kterém právě spouští kód. `Me` se chová jako objektová proměnná nebo proměnná struktury odkaz na aktuální instanci. Pomocí `Me` je obzvláště užitečné pro předávání informací o aktuálně spuštěném instanci třídy nebo struktury do procedury v jiné třídy, struktury nebo modulu.  
  
 Předpokládejme například, že máte následující postup v modulu.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Můžete volat tento postup a předejte aktuální instancí třídy <xref:System.Windows.Forms.Form> třídy jako argument pomocí následujícího příkazu.  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 `My` Funkce poskytuje jednoduché a intuitivní přístup k několika [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy, povolení uživatele jazyka Visual Basic k interakci s počítačem, aplikace, nastavení, prostředky a tak dále.  
  
## <a name="mybase"></a>MyBase  
 `MyBase` – Klíčové slovo se chová jako proměnná objektu odkazuje na základní třídu aktuální instance třídy. `MyBase` běžně se používá pro přístup ke členům základní třídy, přepsat nebo Stínovaný v odvozené třídě. `MyBase.New` umožňuje explicitně volat konstruktor základní třídy v konstruktoru odvozené třídy.  
  
## <a name="myclass"></a>MyClass  
 `MyClass` – Klíčové slovo se chová jako odkaz na aktuální instanci třídy, jak byly původně implementované proměnné objektu. `MyClass` je podobný `Me`, ale všechna volání metody na něm zacházeno, jako kdyby byly metodu `NotOverridable`.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
