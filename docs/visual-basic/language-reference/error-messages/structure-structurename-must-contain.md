---
title: "Struktura & č. 39; &lt;%{structurename/&gt;& č. 39; musí obsahovat alespoň jednu instanci členské proměnné nebo deklaraci události alespoň jedna instance nesmí být označený & č. 39; Vlastní & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords: BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="97465-102">Struktura & č. 39; &lt;%{structurename/&gt;& č. 39; musí obsahovat alespoň jednu instanci členské proměnné nebo deklaraci události alespoň jedna instance nesmí být označený & č. 39; Vlastní & č. 39;</span><span class="sxs-lookup"><span data-stu-id="97465-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="97465-103">Definice struktury nezahrnuje všechny sdíleném proměnné nebo sdíleném nevlastní události.</span><span class="sxs-lookup"><span data-stu-id="97465-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="97465-104">Proměnné nebo událost, která platí pro každou konkrétní instanci místo (sdíleném) na všechny instance souhrnně musí mít každý struktura ([sdílené](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="97465-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="97465-105">Sdíleném konstanty, vlastnosti a postupů nevyhovují tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="97465-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="97465-106">Kromě toho, pokud nejsou žádné sdíleném proměnné a jenom jedna sdíleném událost, že událost nemůže být `Custom` událostí.</span><span class="sxs-lookup"><span data-stu-id="97465-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="97465-107">**ID chyby:** BC30941</span><span class="sxs-lookup"><span data-stu-id="97465-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97465-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="97465-108">To correct this error</span></span>  
  
-   <span data-ttu-id="97465-109">Zadejte alespoň jednu proměnnou nebo událost, která není `Shared`.</span><span class="sxs-lookup"><span data-stu-id="97465-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="97465-110">Pokud definujete jen jednu událost, musí být nevlastní, jakož i sdíleném.</span><span class="sxs-lookup"><span data-stu-id="97465-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97465-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="97465-111">See Also</span></span>  
 [<span data-ttu-id="97465-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="97465-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="97465-113">Postupy: definice struktury</span><span class="sxs-lookup"><span data-stu-id="97465-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="97465-114">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="97465-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
