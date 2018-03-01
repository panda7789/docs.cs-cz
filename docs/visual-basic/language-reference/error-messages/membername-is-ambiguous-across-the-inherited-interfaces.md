---
title: "& č. 39; &lt;membername&gt;& č. 39; je nejednoznačný přes rozhraní zděděné & č. 39;&lt; interfacename1&gt;& č. 39; a & č. 39;&lt; interfacename2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bf4a9c263fd197cdd5d5b4886ee18e2ff112488
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-is-ambiguous-across-the-inherited-interfaces-39ltinterfacename1gt39-and-39ltinterfacename2gt39"></a>& č. 39; &lt;membername&gt;& č. 39; je nejednoznačný přes rozhraní zděděné & č. 39;&lt; interfacename1&gt;& č. 39; a & č. 39;&lt; interfacename2&gt;& č. 39;
Rozhraní dědí z více rozhraní dvě nebo více členů se stejným názvem.  
  
 **ID chyby:** BC30685  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Převést hodnotu na základní rozhraní, které chcete použít; například:  
  
    ```  
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
  
## <a name="see-also"></a>Viz také  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
