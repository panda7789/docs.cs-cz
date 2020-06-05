---
title: Typ '<typename>' není definován.
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 89e2d1d18b456c96f62d6b9ee1dd8dc9d41bf665
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386929"
---
# <a name="type-typename-is-not-defined"></a><span data-ttu-id="3b4bc-102">Typ '\<typename>' není definován.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-102">Type '\<typename>' is not defined</span></span>
<span data-ttu-id="3b4bc-103">Příkaz provedl odkaz na typ, který nebyl definován.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="3b4bc-104">Můžete definovat typ v příkazu deklarace `Enum` , jako je,, `Structure` `Class` nebo `Interface` .</span><span class="sxs-lookup"><span data-stu-id="3b4bc-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="3b4bc-105">**ID chyby:** BC30002</span><span class="sxs-lookup"><span data-stu-id="3b4bc-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3b4bc-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3b4bc-106">To correct this error</span></span>  
  
- <span data-ttu-id="3b4bc-107">Zajistěte, aby definice typu a jejich odkazy používaly stejný pravopis.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
- <span data-ttu-id="3b4bc-108">Ujistěte se, že je pro odkaz k dispozici definice typu.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="3b4bc-109">Například pokud je typ v jiném modulu a byl deklarován `Private` , přesuňte definici typu na odkazující modul nebo deklaraci `Public` .</span><span class="sxs-lookup"><span data-stu-id="3b4bc-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
- <span data-ttu-id="3b4bc-110">Ujistěte se, že obor názvů tohoto typu není předefinován v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="3b4bc-111">Pokud je, použijte `Global` klíčové slovo k úplnému zařazení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="3b4bc-112">Například pokud projekt definuje obor názvů s názvem `System` , <xref:System.Object?displayProperty=nameWithType> typ není k dispozici, pokud není plně kvalifikován pomocí `Global` klíčového slova: `Global.System.Object` .</span><span class="sxs-lookup"><span data-stu-id="3b4bc-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
- <span data-ttu-id="3b4bc-113">Pokud je definován typ, ale knihovna objektů nebo knihovna typů, ve které je definována, není registrována v Visual Basic, klikněte na tlačítko **Přidat odkaz** v nabídce **projekt** a vyberte příslušnou knihovnu objektů nebo knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
- <span data-ttu-id="3b4bc-114">Zajistěte, aby byl typ v sestavení, které je součástí cílového .NET Framework profilu.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="3b4bc-115">Další informace najdete v tématu [řešení potíží s chybami cílení .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="3b4bc-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b4bc-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b4bc-116">See also</span></span>

- [<span data-ttu-id="3b4bc-117">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b4bc-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="3b4bc-118">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="3b4bc-118">Enum Statement</span></span>](../statements/enum-statement.md)
- [<span data-ttu-id="3b4bc-119">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="3b4bc-119">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="3b4bc-120">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="3b4bc-120">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="3b4bc-121">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="3b4bc-121">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="3b4bc-122">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="3b4bc-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
