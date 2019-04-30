---
title: Volitelné parametry musí určovat výchozí hodnotu.
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 01c0abb366e8605a9b153333e645fc3276b6bd16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772590"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="31f4a-102">Volitelné parametry musí určovat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="31f4a-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="31f4a-103">Volitelné parametry musí poskytovat výchozí hodnoty, které lze použít, pokud parametr není zadána ve volání procedury.</span><span class="sxs-lookup"><span data-stu-id="31f4a-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="31f4a-104">**ID chyby:** BC30812</span><span class="sxs-lookup"><span data-stu-id="31f4a-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31f4a-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="31f4a-105">To correct this error</span></span>  
  
- <span data-ttu-id="31f4a-106">Určení výchozích hodnot pro volitelné parametry. Příklad:</span><span class="sxs-lookup"><span data-stu-id="31f4a-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="31f4a-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31f4a-107">See also</span></span>

- [<span data-ttu-id="31f4a-108">Optional</span><span class="sxs-lookup"><span data-stu-id="31f4a-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
