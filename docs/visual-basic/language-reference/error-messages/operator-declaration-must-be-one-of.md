---
title: "Operátor musí být jeden z: +,-, *,-, -, ^, &amp;, jako Mod a, nebo Xor, ne, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;= IsFalse CType, IsTrue –"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords: BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="0624d-102">Operátor musí být jeden z: +,-, *,\,/, ^, &amp;, jako Mod a, nebo Xor, ne, &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="0624d-102">Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="0624d-103">Lze deklarovat pouze operátor, který je vhodné pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="0624d-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="0624d-104">Následující tabulka uvádí operátory, které můžou deklarovat.</span><span class="sxs-lookup"><span data-stu-id="0624d-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="0624d-105">Typ</span><span class="sxs-lookup"><span data-stu-id="0624d-105">Type</span></span>|<span data-ttu-id="0624d-106">Operátory</span><span class="sxs-lookup"><span data-stu-id="0624d-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="0624d-107">Unární</span><span class="sxs-lookup"><span data-stu-id="0624d-107">Unary</span></span>|<span data-ttu-id="0624d-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="0624d-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="0624d-109">binární</span><span class="sxs-lookup"><span data-stu-id="0624d-109">Binary</span></span>|<span data-ttu-id="0624d-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="0624d-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="0624d-111">Převod (unární)</span><span class="sxs-lookup"><span data-stu-id="0624d-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="0624d-112">Všimněte si, že `=` operátor v seznamu binární je relační operátor, operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0624d-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="0624d-113">**ID chyby:** BC33000</span><span class="sxs-lookup"><span data-stu-id="0624d-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0624d-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0624d-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="0624d-115">Vyberte operátor ze sady přetížitelné operátory.</span><span class="sxs-lookup"><span data-stu-id="0624d-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="0624d-116">Pokud potřebujete funkci přetížení operátor, který nelze přímo přetížení, vytvořte `Function` postup, který mají příslušné parametry a vrátí odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0624d-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0624d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0624d-117">See Also</span></span>  
 [<span data-ttu-id="0624d-118">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="0624d-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="0624d-119">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="0624d-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="0624d-120">Postupy: definice operátora</span><span class="sxs-lookup"><span data-stu-id="0624d-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="0624d-121">Postupy: definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="0624d-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="0624d-122">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="0624d-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
