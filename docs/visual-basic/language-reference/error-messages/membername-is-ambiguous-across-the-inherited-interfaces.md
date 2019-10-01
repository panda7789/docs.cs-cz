---
title: Název '<membername>' je dvojznačný ve zděděných rozhraních '<interfacename1>' a '<interfacename2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 06e0d8863c74041f81977b3187fe99a1d05bcd53
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700883"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a>' \<membername > ' je dvojznačný ve zděděných rozhraních ' \<interfacename1 > ' a ' \<interfacename2 > '
Rozhraní dědí dva nebo více členů se stejným názvem z více rozhraní.  
  
 **ID chyby:** BC30685  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přetypování hodnoty na základní rozhraní, které chcete použít; například:  
  
    ```vb  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
