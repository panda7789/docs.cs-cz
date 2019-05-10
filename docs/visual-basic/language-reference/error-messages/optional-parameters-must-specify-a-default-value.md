---
title: Volitelné parametry musí určovat výchozí hodnotu.
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 0f501b518d5b3f2d48ced33885da2afd353c609e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665678"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="f9b51-102">Volitelné parametry musí určovat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f9b51-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="f9b51-103">Volitelné parametry musí poskytovat výchozí hodnoty, které lze použít, pokud parametr není zadána ve volání procedury.</span><span class="sxs-lookup"><span data-stu-id="f9b51-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="f9b51-104">**ID chyby:** BC30812</span><span class="sxs-lookup"><span data-stu-id="f9b51-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f9b51-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f9b51-105">To correct this error</span></span>  
  
- <span data-ttu-id="f9b51-106">Určení výchozích hodnot pro volitelné parametry. Příklad:</span><span class="sxs-lookup"><span data-stu-id="f9b51-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f9b51-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9b51-107">See also</span></span>

- [<span data-ttu-id="f9b51-108">Optional</span><span class="sxs-lookup"><span data-stu-id="f9b51-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
