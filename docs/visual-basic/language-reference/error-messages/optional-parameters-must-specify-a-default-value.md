---
title: "Volitelné parametry musí určovat výchozí hodnotu."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords: BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e9ec6d044ba0a1bb904030ddbb4c4fa406c3ba63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="0a96f-102">Volitelné parametry musí určovat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0a96f-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="0a96f-103">Volitelné parametry musí zadat výchozí hodnoty, které lze použít, pokud je zadaný žádný parametr ve volání procedury.</span><span class="sxs-lookup"><span data-stu-id="0a96f-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="0a96f-104">**ID chyby:** BC30812</span><span class="sxs-lookup"><span data-stu-id="0a96f-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a96f-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0a96f-105">To correct this error</span></span>  
  
-   <span data-ttu-id="0a96f-106">Zadejte výchozí hodnoty pro volitelné parametry; například:</span><span class="sxs-lookup"><span data-stu-id="0a96f-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0a96f-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a96f-107">See Also</span></span>  
 [<span data-ttu-id="0a96f-108">Volitelné</span><span class="sxs-lookup"><span data-stu-id="0a96f-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
