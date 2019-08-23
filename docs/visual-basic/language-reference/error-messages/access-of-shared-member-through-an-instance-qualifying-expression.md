---
title: Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 3174d463744303e8c90ed0b2e1a4d86ed08fbcfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947702"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
Instance proměnné třídy nebo struktury se používá pro přístup `Shared` k proměnné, vlastnosti, proceduře nebo události, které jsou definovány v této třídě nebo struktuře. Toto upozornění může nastat také v případě, že proměnná instance slouží k přístupu k implicitnímu sdílenému členu třídy nebo struktury, jako je například konstanta nebo výčet nebo vnořená třída nebo struktura.  
  
 Účelem sdílení člena je vytvořit pouze jednu kopii daného člena a učinit jednu kopii k dispozici pro každou instanci třídy nebo struktury, ve které je deklarována. Je v souladu s tímto účelem pro přístup `Shared` ke členu prostřednictvím názvu jeho třídy nebo struktury, nikoli prostřednictvím proměnné, která obsahuje jednotlivou instanci dané třídy nebo struktury.  
  
 Přístup ke `Shared` členu prostřednictvím proměnné instance může ztížit pochopení kódu tím, že zakrývá skutečnost, že je `Shared`členem. Kromě toho, pokud je takový přístup součástí výrazu, který provádí jiné akce, jako je `Function` například procedura, která vrací instanci sdíleného člena, Visual Basic obejít výraz a jakékoli další akce, které by jinak prováděly.  
  
 Další informace a příklad najdete v tématu [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte název třídy nebo struktury, který definuje `Shared` člena k přístupu, jak je znázorněno v následujícím příkladu.  
  
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
> Pokud dva programovací prvky mají stejný název, je třeba upozornit na účinky rozsahu. V předchozím příkladu, pokud deklarujete instanci pomocí `Dim testClass as testClass = Nothing`, kompilátor zpracovává `testClass.sayHello()` volání jako přístup k metodě přes název třídy a nedochází k žádnému upozornění.  
  
## <a name="see-also"></a>Viz také:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Obor v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
