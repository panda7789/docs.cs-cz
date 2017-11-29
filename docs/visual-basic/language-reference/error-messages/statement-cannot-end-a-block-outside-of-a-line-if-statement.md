---
title: "Příkaz nemůže ukončit blok mimo řádek & č. 39; Pokud & č. 39; příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords: BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="63416-102">Příkaz nemůže ukončit blok mimo řádek & č. 39; Pokud & č. 39; příkaz</span><span class="sxs-lookup"><span data-stu-id="63416-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="63416-103">Jeden řádek `If` příkaz obsahuje několik příkazů oddělené dvojtečkou (:), z nichž jeden je `End` příkaz pro řídicí blok mimo jeden řádek `If`.</span><span class="sxs-lookup"><span data-stu-id="63416-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="63416-104">Jeden řádek `If` příkazy se nedoporučuje používat `End If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="63416-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="63416-105">**ID chyby:** BC32005</span><span class="sxs-lookup"><span data-stu-id="63416-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="63416-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="63416-106">To correct this error</span></span>  
  
-   <span data-ttu-id="63416-107">Přesunout jednom řádku `If` příkaz mimo řídicí blok, který obsahuje `End If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="63416-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63416-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="63416-108">See Also</span></span>  
 [<span data-ttu-id="63416-109">If... Potom... Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="63416-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
