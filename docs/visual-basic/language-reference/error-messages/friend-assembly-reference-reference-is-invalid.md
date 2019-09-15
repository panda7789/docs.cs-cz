---
title: Odkaz na sestavení typu <reference> Friend není platný.
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972393"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="08e5b-102">\<Referenční > odkazu na sestavení typu Friend je neplatný.</span><span class="sxs-lookup"><span data-stu-id="08e5b-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="08e5b-103">> Odkazu na \<odkaz na sestavení typu Friend je neplatný.</span><span class="sxs-lookup"><span data-stu-id="08e5b-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="08e5b-104">Sestavení podepsaná silným názvem musí v deklaracích InternalsVisibleTo určovat veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="08e5b-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="08e5b-105">Název sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu identifikuje sestavení se silným názvem, ale `PublicKey` nezahrnuje atribut.</span><span class="sxs-lookup"><span data-stu-id="08e5b-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="08e5b-106">**ID chyby:** BC31535</span><span class="sxs-lookup"><span data-stu-id="08e5b-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08e5b-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="08e5b-107">To correct this error</span></span>  
  
1. <span data-ttu-id="08e5b-108">Určete veřejný klíč pro sestavení typu Friend se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="08e5b-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="08e5b-109">Zahrňte veřejný klíč jako součást názvu sestavení předaného <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu `PublicKey` pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="08e5b-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e5b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08e5b-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="08e5b-111">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="08e5b-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
