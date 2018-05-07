---
title: Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 035882b60c90d9a6141ad0d34b4c40682e0c32a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
Proměnnou instance třídy nebo struktura slouží k přístupu `Shared` proměnnou, vlastnost, postup nebo událostí, které jsou definované v tomto třídu nebo strukturu. Toto upozornění se může také nastat, pokud proměnnou instance se používá pro přístup implicitně sdíleného člena třídy nebo struktuře, například konstanta nebo výčtu nebo vnořenou třídu nebo strukturu.  
  
 Účelem sdílení členem je vytvořit pouze jednu kopii tohoto člena a ujistěte se, že jedna kopie k dispozici pro všechny instance řetězce třídu nebo strukturu, ve kterém je deklarovaná. Je v souladu s pro přístup k tomuto účelu `Shared` člen prostřednictvím název jeho třídu nebo strukturu, a nikoli prostřednictvím proměnné, která obsahuje jednotlivé instance třídy nebo struktura.  
  
 Přístup k `Shared` člena prostřednictvím instance proměnné můžete byl váš kód více těžko srozumitelné zakódováním skutečnost, že je člen `Shared`. Kromě toho pokud tento přístup je součástí výrazu, která přistupuje jiné akce, například `Function` procedury, která vrátí instanci sdíleného člena, Visual Basic obchází ve výrazu a všechny akce, které by jinak provedl.  
  
 Další informace a příklady naleznete v tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použijte název třídy nebo struktura, která definuje `Shared` člen k přístupu, jak je znázorněno v následujícím příkladu.  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  Být výstraha pro důsledky oboru, pokud dva programovací elementy mají stejný název. V předchozím příkladu, pokud deklarace instance pomocí `Dim testClass as testClass = Nothing`, kompilátor zpracovává volání `testClass.sayHello()` jako dochází přístupu metody pomocí názvu třídy a bez upozornění.  
  
## <a name="see-also"></a>Viz také  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Rozsah v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
