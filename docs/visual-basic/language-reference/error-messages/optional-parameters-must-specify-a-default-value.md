---
title: Volitelné parametry musí určovat výchozí hodnotu.
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 8ec4627d070cc670ce04be3a5d0298dba0a279d0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582136"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="b4651-102">Volitelné parametry musí určovat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b4651-102">Optional parameters must specify a default value</span></span>

<span data-ttu-id="b4651-103">Volitelné parametry musí poskytovat výchozí hodnoty, které lze použít, pokud není žádný parametr zadán procedurou volání.</span><span class="sxs-lookup"><span data-stu-id="b4651-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="b4651-104">**ID chyby:** BC30812</span><span class="sxs-lookup"><span data-stu-id="b4651-104">**Error ID:** BC30812</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b4651-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b4651-105">To correct this error</span></span>

<span data-ttu-id="b4651-106">Zadejte výchozí hodnoty pro volitelné parametry; například:</span><span class="sxs-lookup"><span data-stu-id="b4651-106">Specify default values for optional parameters; for example:</span></span>

```vb
Sub Proc1(ByVal X As Integer,
      Optional ByVal Y As String = "Default Value")
    MsgBox("Default argument is: " & Y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="b4651-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4651-107">See also</span></span>

- [<span data-ttu-id="b4651-108">Optional</span><span class="sxs-lookup"><span data-stu-id="b4651-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
