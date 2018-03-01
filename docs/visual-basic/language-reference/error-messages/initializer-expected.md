---
title: "Byl očekáván inicializátor."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46ff91ec240212571f7ec9f26e82d9d128263545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="initializer-expected"></a><span data-ttu-id="0fe84-102">Byl očekáván inicializátor.</span><span class="sxs-lookup"><span data-stu-id="0fe84-102">Initializer expected</span></span>
<span data-ttu-id="0fe84-103">Pokusili jste se deklarujte instanci třídy pomocí inicializátoru objektu, ve kterém inicializace seznam je prázdný, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0fe84-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="0fe84-104">Minimálně jedno pole nebo vlastnost musí být inicializován v inicializátoru seznamu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0fe84-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="0fe84-105">**ID chyby:** BC30996</span><span class="sxs-lookup"><span data-stu-id="0fe84-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0fe84-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0fe84-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="0fe84-107">Inicializace alespoň jednoho pole nebo vlastnost inicializátoru, nebo nepoužívejte inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="0fe84-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe84-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fe84-108">See Also</span></span>  
 [<span data-ttu-id="0fe84-109">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="0fe84-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="0fe84-110">Postupy: Deklarace objektu pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="0fe84-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
