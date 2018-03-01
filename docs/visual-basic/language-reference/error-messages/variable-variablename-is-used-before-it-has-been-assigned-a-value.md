---
title: "Proměnná & č. 39; &lt;NázevProměnné&gt;& č. 39; před byla přiřazena hodnota je používána"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="d5409-102">Proměnná & č. 39; &lt;NázevProměnné&gt;& č. 39; před byla přiřazena hodnota je používána</span><span class="sxs-lookup"><span data-stu-id="d5409-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="d5409-103">Proměnnou '\<NázevProměnné > se před byla přiřazena hodnota je používána.</span><span class="sxs-lookup"><span data-stu-id="d5409-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="d5409-104">V době běhu může způsobit výjimka odkazu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d5409-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="d5409-105">Aplikace má alespoň jednu cestu možný prostřednictvím jeho kódu, který čte proměnné předtím, než je k němu přiřazen žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d5409-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="d5409-106">Pokud proměnnou nikdy byla přiřazena hodnota, obsahuje výchozí hodnotu pro jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="d5409-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="d5409-107">Pro odkaz na datový typ, že výchozí hodnota je [nic](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="d5409-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="d5409-108">Čtení referenční proměnné, která má hodnotu `Nothing` může způsobit <xref:System.NullReferenceException> v některých případech.</span><span class="sxs-lookup"><span data-stu-id="d5409-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="d5409-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="d5409-109">By default, this message is a warning.</span></span> <span data-ttu-id="d5409-110">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d5409-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d5409-111">**ID chyby:** BC42104</span><span class="sxs-lookup"><span data-stu-id="d5409-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5409-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d5409-112">To correct this error</span></span>  
  
-   <span data-ttu-id="d5409-113">Zkontrolujte logika toku řízení a ujistěte se, že proměnná nemá platnou hodnotu před ovládací prvek předává do jakékoli příkaz, který čte ho.</span><span class="sxs-lookup"><span data-stu-id="d5409-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="d5409-114">Jedním ze způsobů zaručit, že má proměnná vždy platnou hodnotu je k chybě při inicializaci součástí jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="d5409-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="d5409-115">V části "Inicializace" v [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5409-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5409-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5409-116">See Also</span></span>  
 [<span data-ttu-id="d5409-117">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="d5409-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="d5409-118">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="d5409-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="d5409-119">Řešení potíží s proměnnými</span><span class="sxs-lookup"><span data-stu-id="d5409-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
