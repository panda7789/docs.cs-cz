---
title: Proměnná '<variablename>' je použita před tím, než jí byla přiřazena hodnota.
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 34718243172d3b1a238a813268e672d62c4eeb6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406531"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="b3b7a-102">Proměnná '\<variablename>' je použita před tím, než jí byla přiřazena hodnota.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-102">Variable '\<variablename>' is used before it has been assigned a value</span></span>
<span data-ttu-id="b3b7a-103">Proměnná ' \<variablename> ' se používá předtím, než se jí přiřadí hodnota.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="b3b7a-104">Výjimka odkazu s hodnotou null by mohla být v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="b3b7a-105">Aplikace má alespoň jednu možnou cestu prostřednictvím kódu, který čte proměnnou před přiřazením jakékoli hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="b3b7a-106">Pokud proměnné nikdy nebyla přiřazena hodnota, obsahuje výchozí hodnotu pro svůj datový typ.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="b3b7a-107">Pro referenční datový typ je tato výchozí hodnota [Nothing](../nothing.md).</span><span class="sxs-lookup"><span data-stu-id="b3b7a-107">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="b3b7a-108">Čtení referenční proměnné, která má hodnotu, `Nothing` může <xref:System.NullReferenceException> v některých případech způsobit určitou situaci.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="b3b7a-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-109">By default, this message is a warning.</span></span> <span data-ttu-id="b3b7a-110">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b3b7a-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b3b7a-111">**ID chyby:** BC42104</span><span class="sxs-lookup"><span data-stu-id="b3b7a-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3b7a-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b3b7a-112">To correct this error</span></span>  
  
- <span data-ttu-id="b3b7a-113">Zkontrolujte logiku toku ovládacích prvků a ujistěte se, že má proměnná platnou hodnotu, než ovládací prvek projde jakýmkoli příkazem, který ho přečte.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
- <span data-ttu-id="b3b7a-114">Jedním ze způsobů, jak zaručit, že proměnná vždy má platnou hodnotu, je ji inicializovat jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="b3b7a-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="b3b7a-115">Viz "inicializace" v [příkazu Dim](../statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b3b7a-115">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b7a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3b7a-116">See also</span></span>

- [<span data-ttu-id="b3b7a-117">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="b3b7a-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="b3b7a-118">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="b3b7a-118">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="b3b7a-119">Řešení potíží s proměnnými</span><span class="sxs-lookup"><span data-stu-id="b3b7a-119">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
