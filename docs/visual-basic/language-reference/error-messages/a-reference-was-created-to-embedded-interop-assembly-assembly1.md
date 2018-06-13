---
title: Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce &#39; &lt;assembly1&gt; &#39; z důvodu nepřímý odkaz na sestavení ze sestavení &#39; &lt;assembly2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 43a441b6b99988ae1b47969dde9c4bc815820767
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588129"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a><span data-ttu-id="8a546-102">Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce &#39; &lt;assembly1&gt; &#39; z důvodu nepřímý odkaz na sestavení ze sestavení &#39; &lt;assembly2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="8a546-102">A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;</span></span>
<span data-ttu-id="8a546-103">Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce se\<assembly1 > se z důvodu nepřímý odkaz na sestavení ze sestavení '\<assembly2 >'.</span><span class="sxs-lookup"><span data-stu-id="8a546-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="8a546-104">Zvažte změnu vlastnost vložit zprostředkovatel komunikace s objekty typy v jednom ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="8a546-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="8a546-105">Přidáte odkaz na sestavení (assembly1), který má `Embed Interop Types` vlastnost nastavena na hodnotu `True`.</span><span class="sxs-lookup"><span data-stu-id="8a546-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="8a546-106">To dává pokyn kompilátoru pro vložení informací o zprostředkovatele komunikace s objekty typu z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="8a546-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="8a546-107">Kompilátor však nemůže vložit spolupráce typ informace z tohoto sestavení, protože jiné sestavení, které se vám (assembly2) také odkazuje dané sestavení (assembly1) a má `Embed Interop Types` vlastnost nastavena na hodnotu `False`.</span><span class="sxs-lookup"><span data-stu-id="8a546-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a546-108">Nastavení `Embed Interop Types` vlastnost na odkaz na sestavení pro `True` je ekvivalentní k odkazování na sestavení s použitím `/link` – možnost kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8a546-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="8a546-109">**ID chyby:** BC40059</span><span class="sxs-lookup"><span data-stu-id="8a546-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="8a546-110">Pro vyřešení tohoto upozornění</span><span class="sxs-lookup"><span data-stu-id="8a546-110">To address this warning</span></span>  
  
-   <span data-ttu-id="8a546-111">Chcete-li vložit informace zprostředkovatele komunikace s objekty typu u obou sestavení, nastavte `Embed Interop Types` vlastnost na všechny odkazy na assembly1 na `True`.</span><span class="sxs-lookup"><span data-stu-id="8a546-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="8a546-112">Chcete-li odebrat upozornění, můžete nastavit `Embed Interop Types` vlastnost assembly1 na `False`.</span><span class="sxs-lookup"><span data-stu-id="8a546-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="8a546-113">V takovém případě zprostředkovatele komunikace s objekty typu informace jsou poskytovány primární spolupracující sestavení (PIA).</span><span class="sxs-lookup"><span data-stu-id="8a546-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a546-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a546-114">See Also</span></span>  
 [<span data-ttu-id="8a546-115">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a546-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="8a546-116">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="8a546-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
