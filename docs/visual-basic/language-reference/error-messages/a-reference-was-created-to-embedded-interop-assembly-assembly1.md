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
ms.openlocfilehash: 0f7a136abb0e63e4b139b87c8f18ae3fcb99dbf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947750"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a><span data-ttu-id="48dc5-102">Byl vytvořen odkaz na vložené definiční sestavení\<assembly1 > z důvodu nepřímého odkazu na toto sestavení ze\<sestavení Assembly2 >.</span><span class="sxs-lookup"><span data-stu-id="48dc5-102">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'</span></span>
<span data-ttu-id="48dc5-103">Byl vytvořen odkaz na vložené sestavení vzájemné spolupráce '\<assembly1 > ' z důvodu nepřímého odkazu na toto sestavení ze sestavení\<' Assembly2 > '.</span><span class="sxs-lookup"><span data-stu-id="48dc5-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="48dc5-104">Zvažte změnu vlastnosti "Embed Interop Types" v obou sestaveních.</span><span class="sxs-lookup"><span data-stu-id="48dc5-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="48dc5-105">Přidali jste odkaz na sestavení (assembly1), které má `Embed Interop Types` vlastnost nastavenou na. `True`</span><span class="sxs-lookup"><span data-stu-id="48dc5-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="48dc5-106">Tento příkaz instruuje kompilátor, aby do tohoto sestavení vložil informace o typu spolupráce.</span><span class="sxs-lookup"><span data-stu-id="48dc5-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="48dc5-107">Kompilátor však nemůže vložit informace o typu spolupráce z tohoto sestavení, protože jiné sestavení, na které jste odkazován (Assembly2), také odkazuje na toto sestavení (assembly1) `Embed Interop Types` a má vlastnost `False`nastavenu na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48dc5-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48dc5-108">Nastavení vlastnosti na `True` odkaz na sestavení je ekvivalentní k odkazování na sestavení pomocí `/link` možnosti pro kompilátor příkazového řádku. `Embed Interop Types`</span><span class="sxs-lookup"><span data-stu-id="48dc5-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="48dc5-109">**ID chyby:** BC40059</span><span class="sxs-lookup"><span data-stu-id="48dc5-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="48dc5-110">Řešení tohoto upozornění</span><span class="sxs-lookup"><span data-stu-id="48dc5-110">To address this warning</span></span>  
  
- <span data-ttu-id="48dc5-111">Pro vložení informací o typu spolupráce pro obě sestavení nastavte `Embed Interop Types` vlastnost na všech odkazech na assembly1 na. `True`</span><span class="sxs-lookup"><span data-stu-id="48dc5-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
- <span data-ttu-id="48dc5-112">Chcete-li odstranit upozornění, můžete nastavit `Embed Interop Types` vlastnost assembly1 na `False`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48dc5-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="48dc5-113">V tomto případě jsou informace o typu spolupráce poskytovány pomocí primárního definičního sestavení (PIA).</span><span class="sxs-lookup"><span data-stu-id="48dc5-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48dc5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48dc5-114">See also</span></span>

- [<span data-ttu-id="48dc5-115">/Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48dc5-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="48dc5-116">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="48dc5-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
