---
title: Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 8e6ddab16c59d7ce95d96b377e3f372f6ebe5278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751602"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
Proměnná instance třídy nebo struktury se používá k přístupu `Shared` proměnná, vlastnost, procedura nebo události definované v této třídě nebo struktuře. Toto upozornění může také dojít, pokud proměnnou instance se používá pro přístup k implicitně sdílenému členu třídy nebo struktury, jako je konstantní nebo výčtu, nebo vnořené třídy nebo struktury.  
  
 Účelem sdílení člen je vytvořit pouze jednu kopii tohoto člena a zadáte jednu kopii k dispozici pro každou instanci třídy nebo struktury, ve kterém je deklarována. Je konzistentní s pro přístup k tomuto účelu `Shared` člen prostřednictvím názvu třídy nebo struktury, a nikoli prostřednictvím proměnné, který obsahuje jednotlivé instance této třídy nebo struktury.  
  
 Přístup k `Shared` člena prostřednictvím instance proměnné může ztížit váš kód pochopit zakódováním skutečnost, že je člen `Shared`. Kromě toho pokud takový přístup je součástí výrazu, který provede další akce, například `Function` proceduru, která vrací instanci sdíleného členu, Visual Basic obchází výraz a všechny akce, které by jinak provedl.  
  
 Další informace a příklad najdete v tématu [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte název třídy nebo struktury, která definuje `Shared` člen k přístupu, jak je znázorněno v následujícím příkladu.  
  
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
>  Být výstraha pro efekty oboru, pokud dva programovací elementy mají stejný název. V předchozím příkladu, je-li deklarována instance pomocí `Dim testClass as testClass = Nothing`, kompilátor zpracovává volání `testClass.sayHello()` jako dochází přístupu metody pomocí názvu třídy a žádné upozornění.  
  
## <a name="see-also"></a>Viz také:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Obor v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
