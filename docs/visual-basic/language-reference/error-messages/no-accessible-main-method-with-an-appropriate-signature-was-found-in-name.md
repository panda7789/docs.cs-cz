---
title: "Žádné dostupné & č. 39; Hlavní & č. 39; nebyla nalezena metoda s odpovídajícím podpisem v & č. 39; &lt;název&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords: BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f45dc17304c3c9d62b65760f2c1b5d461812a66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="d0f31-102">Žádné dostupné & č. 39; Hlavní & č. 39; nebyla nalezena metoda s odpovídajícím podpisem v & č. 39; &lt;název&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="d0f31-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="d0f31-103">Aplikace příkazového řádku musí mít `Sub Main` definované.</span><span class="sxs-lookup"><span data-stu-id="d0f31-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="d0f31-104">`Main`musí být deklarována jako `Public Shared` Pokud je definována v třídě nebo jako `Public` Pokud definovaná v modulu.</span><span class="sxs-lookup"><span data-stu-id="d0f31-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="d0f31-105">Další informace o `Main`, najdete v části [NIB: Visual Basic verze z Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).</span><span class="sxs-lookup"><span data-stu-id="d0f31-105">For more information on `Main`, see [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).</span></span>  
  
 <span data-ttu-id="d0f31-106">**ID chyby:** BC30737</span><span class="sxs-lookup"><span data-stu-id="d0f31-106">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d0f31-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d0f31-107">To correct this error</span></span>  
  
-   <span data-ttu-id="d0f31-108">Definování `Public Sub Main` postup pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="d0f31-108">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="d0f31-109">Deklarujte ji jako `Shared` jenom v případě můžete definovat uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="d0f31-109">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f31-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0f31-110">See Also</span></span>  
 [<span data-ttu-id="d0f31-111">NIB: verze jazyka Visual Basic Hello, World</span><span class="sxs-lookup"><span data-stu-id="d0f31-111">NIB: Visual Basic Version of Hello, World</span></span>](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [<span data-ttu-id="d0f31-112">Struktura programu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0f31-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="d0f31-113">Postupy</span><span class="sxs-lookup"><span data-stu-id="d0f31-113">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
