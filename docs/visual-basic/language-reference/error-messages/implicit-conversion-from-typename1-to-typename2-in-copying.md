---
title: "Implicitní převod z & č. 39; &lt;NázevTypu1&gt;& č. 39; na & č. 39;&lt; NázevTypu2&gt;& č. 39; kopírování hodnotu & č. 39; ByRef & č. 39; Parametr & č. 39; &lt;parametername&gt;& č. 39; zpět na odpovídající argument."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords: BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Implicitní převod z & č. 39; &lt;NázevTypu1&gt;& č. 39; na & č. 39;&lt; NázevTypu2&gt;& č. 39; kopírování hodnotu & č. 39; ByRef & č. 39; Parametr & č. 39; &lt;parametername&gt;& č. 39; zpět na odpovídající argument.
Postup je volán s [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument jiného typu než jeho odpovídající parametr.  
  
 Pokud předáte argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] někdy zkopíruje hodnota argumentu do místní proměnné v postupu neprochází odkaz. V takovém případě, když se proces vrátí [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zpět do argument ve volání kód musí zkopírujte místní hodnotu proměnné.  
  
 Pokud `ByRef` hodnota argumentu se zkopíruje do procesu a argumentů a parametrů jsou stejného typu, je nutné žádný převod. Pokud se typy liší, ale [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nutné převést v obou směrech. Vzhledem k tomu, že nemůžete použít `CType` nebo některý z dalších převod slov v argumentu procedury nebo parametr, takový převod je vždy implicitní.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC41999  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je to možné, použijte volání argument stejného typu jako parametr postupu, takže [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] není nutné provádět jakékoli převody.  
  
-   Pokud potřebujete volání procedury s argumentem, zadejte odlišný od typu parametru ale nemusíte vrátit hodnotu do volání argument, definujte parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) místo `ByRef`.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry a argumenty procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Předávání argumentů podle hodnoty a podle Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
