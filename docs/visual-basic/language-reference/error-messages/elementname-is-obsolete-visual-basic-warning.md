---
title: "& č. 39; &lt;elementname&gt;& č. 39; je zastaralé (upozornění Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords: BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd6580da794255a3324021a284816ef9700beee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="f1d21-102">& č. 39; &lt;elementname&gt;& č. 39; je zastaralé (upozornění Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1d21-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="f1d21-103">Příkaz pokusí o přístup k programovací element, který byl označen s <xref:System.ObsoleteAttribute> atribut a direktiva považováno za upozornění.</span><span class="sxs-lookup"><span data-stu-id="f1d21-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="f1d21-104">Můžete označit jakékoli programovací element se už používá použitím <xref:System.ObsoleteAttribute> k němu.</span><span class="sxs-lookup"><span data-stu-id="f1d21-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="f1d21-105">Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost, která má buď `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="f1d21-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="f1d21-106">Pokud je nastavena na `True`, kompilátor zpracovává pokus o použití elementu za chybu.</span><span class="sxs-lookup"><span data-stu-id="f1d21-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="f1d21-107">Pokud je nastavena na `False`, nebo ho nechte výchozí `False`, kompilátor vydá upozornění, pokud dojde pokusu o použití elementu.</span><span class="sxs-lookup"><span data-stu-id="f1d21-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="f1d21-108">Ve výchozím nastavení, tato zpráva je upozornění, protože <xref:System.ObsoleteAttribute.IsError%2A> vlastnost <xref:System.ObsoleteAttribute> je `False`.</span><span class="sxs-lookup"><span data-stu-id="f1d21-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="f1d21-109">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f1d21-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f1d21-110">**ID chyby:** BC40008</span><span class="sxs-lookup"><span data-stu-id="f1d21-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1d21-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f1d21-111">To correct this error</span></span>  
  
-   <span data-ttu-id="f1d21-112">Ujistěte se, že je odkaz na zdrojový kód pravopis název elementu správně.</span><span class="sxs-lookup"><span data-stu-id="f1d21-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d21-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1d21-113">See Also</span></span>  
 [<span data-ttu-id="f1d21-114">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="f1d21-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
