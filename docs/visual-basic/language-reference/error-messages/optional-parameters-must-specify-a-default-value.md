---
title: Volitelné parametry musí určovat výchozí hodnotu.
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: eb782b2fa1fb73c7407b57a0942e5eebb30474ff
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040928"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="9d727-102">Volitelné parametry musí určovat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9d727-102">Optional parameters must specify a default value</span></span>

<span data-ttu-id="9d727-103">Volitelné parametry musí poskytovat výchozí hodnoty, které lze použít, pokud není žádný parametr zadán procedurou volání.</span><span class="sxs-lookup"><span data-stu-id="9d727-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="9d727-104">**ID chyby:** BC30812</span><span class="sxs-lookup"><span data-stu-id="9d727-104">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="9d727-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d727-105">Example</span></span>

<span data-ttu-id="9d727-106">Následující příklad generuje BC30812:</span><span class="sxs-lookup"><span data-stu-id="9d727-106">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="9d727-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9d727-107">To correct this error</span></span>

<span data-ttu-id="9d727-108">Zadejte výchozí hodnoty pro volitelné parametry:</span><span class="sxs-lookup"><span data-stu-id="9d727-108">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="9d727-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d727-109">See also</span></span>

- [<span data-ttu-id="9d727-110">Optional</span><span class="sxs-lookup"><span data-stu-id="9d727-110">Optional</span></span>](../modifiers/optional.md)
