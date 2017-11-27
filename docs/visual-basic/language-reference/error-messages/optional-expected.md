---
title: "& č. 39; volitelné & č. 39; očekávání"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords: BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e84371935fdd2d558e6828c05fa952b9cc4cf4f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39optional39-expected"></a><span data-ttu-id="f72cb-102">& č. 39; volitelné & č. 39; očekávání</span><span class="sxs-lookup"><span data-stu-id="f72cb-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="f72cb-103">Požadovaný argument následuje za volitelným argumentem v deklaraci postupu.</span><span class="sxs-lookup"><span data-stu-id="f72cb-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="f72cb-104">Každý argument za volitelným argumentem musí být také volitelné.</span><span class="sxs-lookup"><span data-stu-id="f72cb-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="f72cb-105">**ID chyby:** BC30202</span><span class="sxs-lookup"><span data-stu-id="f72cb-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f72cb-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f72cb-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f72cb-107">Pokud je argument bude vyžadovat, přesuňte jej na atributy stála před první nepovinný argument v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="f72cb-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="f72cb-108">Pokud argument má být volitelné, použijte `Optional` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f72cb-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72cb-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="f72cb-109">See Also</span></span>  
 [<span data-ttu-id="f72cb-110">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="f72cb-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
