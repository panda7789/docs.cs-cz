---
title: "& č. 39; Modul & č. 39; příkazy lze používat pouze na úrovni souboru nebo oboru názvů"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61fe12fbd7d20e6cd2b6bc464e7fc3293150213b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="0f48d-102">& č. 39; Modul & č. 39; příkazy lze používat pouze na úrovni souboru nebo oboru názvů</span><span class="sxs-lookup"><span data-stu-id="0f48d-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="0f48d-103">`Module`příkazy musí být v horní části souboru zdroje ihned po `Option` a `Imports` příkazy, globálními atributy a deklarace oboru názvů, ale před všechny ostatní deklarace.</span><span class="sxs-lookup"><span data-stu-id="0f48d-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="0f48d-104">**ID chyby:** BC30617</span><span class="sxs-lookup"><span data-stu-id="0f48d-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f48d-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0f48d-105">To correct this error</span></span>  
  
-   <span data-ttu-id="0f48d-106">Přesunout `Module` příkaz na začátek oboru názvů deklarace nebo zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="0f48d-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f48d-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f48d-107">See Also</span></span>  
 [<span data-ttu-id="0f48d-108">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="0f48d-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
