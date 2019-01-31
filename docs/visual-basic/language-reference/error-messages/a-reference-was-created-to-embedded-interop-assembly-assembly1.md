---
title: Byl vytvořen odkaz na vložené definiční sestavení '<assembly1>' z důvodu nepřímého odkazu na toto sestavení ze sestavení '<assembly2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 058aa4891d05147756290affd60ea5fb260c33ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262949"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a><span data-ttu-id="09e67-102">Vytvořil se odkaz na vložené definiční sestavení "\<assembly1 >" z důvodu nepřímého odkazu na toto sestavení ze sestavení '\<assembly2 > "</span><span class="sxs-lookup"><span data-stu-id="09e67-102">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'</span></span>
<span data-ttu-id="09e67-103">Vytvořil se odkaz na vložené definiční sestavení "\<assembly1 >" z důvodu nepřímého odkazu na toto sestavení ze sestavení '\<assembly2 > ".</span><span class="sxs-lookup"><span data-stu-id="09e67-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="09e67-104">Zvažte změnu vlastnosti 'Vložit typy spolupráce' u obou sestavení.</span><span class="sxs-lookup"><span data-stu-id="09e67-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="09e67-105">Přidáte odkaz na sestavení (assembly1), který má `Embed Interop Types` nastavenou na `True`.</span><span class="sxs-lookup"><span data-stu-id="09e67-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="09e67-106">Toto dá pokyn kompilátoru k vložení typu spolupráce informace z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="09e67-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="09e67-107">Kompilátor však nelze vložit informace o typu spolupráce ze sestavení, protože jiné sestavení, které se vám (assembly2) také odkazuje na sestavení (assembly1) a má `Embed Interop Types` nastavenou na `False`.</span><span class="sxs-lookup"><span data-stu-id="09e67-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09e67-108">Nastavení `Embed Interop Types` vlastnost na odkaz na sestavení do `True` je ekvivalentní k odkazování na sestavení s použitím `/link` – možnost kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="09e67-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="09e67-109">**ID chyby:** BC40059</span><span class="sxs-lookup"><span data-stu-id="09e67-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="09e67-110">Chcete-li vyřešit tato upozornění</span><span class="sxs-lookup"><span data-stu-id="09e67-110">To address this warning</span></span>  
  
-   <span data-ttu-id="09e67-111">Chcete-li vložit informace o typu spolupráce u obou sestavení, nastavte `Embed Interop Types` vlastnost u všech odkazů na assembly1 na `True`.</span><span class="sxs-lookup"><span data-stu-id="09e67-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="09e67-112">Chcete-li odebrat upozornění, můžete nastavit `Embed Interop Types` vlastnost assembly1 na `False`.</span><span class="sxs-lookup"><span data-stu-id="09e67-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="09e67-113">Informace o typu spolupráce v tomto případě poskytuje primární definiční sestavení (PIA).</span><span class="sxs-lookup"><span data-stu-id="09e67-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e67-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09e67-114">See also</span></span>
- [<span data-ttu-id="09e67-115">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09e67-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="09e67-116">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="09e67-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
