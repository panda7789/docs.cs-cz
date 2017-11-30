---
title: "Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords: BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0635e1b18b24a241fabad6d67da34f8dde9530db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="1607e-102">Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.</span><span class="sxs-lookup"><span data-stu-id="1607e-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="1607e-103">A `For Each` smyčky používá pole jako jeho *element* proměnné iterace ale inicializuje tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="1607e-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="1607e-104">Následující příkazy ukazují, jak může být generována této chybě.</span><span class="sxs-lookup"><span data-stu-id="1607e-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="1607e-105">První `For Each` příkaz je správný způsob, jak přístup prvky `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="1607e-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="1607e-106">Druhý `For Each` příkaz vygeneruje tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="1607e-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="1607e-107">**ID chyby:** BC32039</span><span class="sxs-lookup"><span data-stu-id="1607e-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1607e-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1607e-108">To correct this error</span></span>  
  
-   <span data-ttu-id="1607e-109">Inicializace odebrání deklaraci *element* proměnné iterace.</span><span class="sxs-lookup"><span data-stu-id="1607e-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1607e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1607e-110">See Also</span></span>  
 [<span data-ttu-id="1607e-111">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="1607e-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="1607e-112">Pole</span><span class="sxs-lookup"><span data-stu-id="1607e-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="1607e-113">Kolekce</span><span class="sxs-lookup"><span data-stu-id="1607e-113">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
