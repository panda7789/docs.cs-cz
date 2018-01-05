---
title: "Postupy: Registrace primárních sestavení spolupráce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6615abdf621217baa7ced4211bfa19abac944be9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-primary-interop-assemblies"></a><span data-ttu-id="b20ff-102">Postupy: Registrace primárních sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="b20ff-102">How to: Register Primary Interop Assemblies</span></span>
<span data-ttu-id="b20ff-103">Třídy mohou být zařazena pouze pomocí zprostředkovatele komunikace s objekty COM a jsou vždycky zařazené jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b20ff-103">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="b20ff-104">V některých případech rozhraní sloužící k zařazování třídy se nazývá rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="b20ff-104">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="b20ff-105">Informace o přepsání třídy rozhraní s rozhraním zvoleného najdete v tématu [obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md).</span><span class="sxs-lookup"><span data-stu-id="b20ff-105">For information about overriding the class interface with an interface of your choice, see [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md).</span></span>  
  
 <span data-ttu-id="b20ff-106">Přestože všechny vývojáře, který chce používat typy modelu COM z aplikace rozhraní .NET Framework můžete vygenerovat sestavení spolupráce, to proto vytvoří problém.</span><span class="sxs-lookup"><span data-stu-id="b20ff-106">Although any developer who wants to use COM types from a .NET Framework application can generate an interop assembly, doing so creates a problem.</span></span> <span data-ttu-id="b20ff-107">Pokaždé, když vývojář importuje a podepisuje knihovny typů modelu COM, která vývojáře vytvoří sadu jedinečné typy, které nejsou kompatibilní s těmi, importovat a podepsaný jiné developer.</span><span class="sxs-lookup"><span data-stu-id="b20ff-107">Each time a developer imports and signs a COM type library, that developer creates a set of unique types that are incompatible with those imported and signed by another developer.</span></span> <span data-ttu-id="b20ff-108">Řešení tohoto problému nekompatibilita typ je pro každý vývojář získat dodavatele a podepsaný primární spolupracující sestavení.</span><span class="sxs-lookup"><span data-stu-id="b20ff-108">The solution to this type incompatibility problem is for each developer to obtain the vendor-supplied and signed primary interop assembly.</span></span>  
  
 <span data-ttu-id="b20ff-109">Pokud máte v plánu vystavit typy modelu COM třetích stran k ostatním aplikacím, vždy používejte primární spolupracující sestavení od stejného vydavatele jako knihovny typů, který definuje.</span><span class="sxs-lookup"><span data-stu-id="b20ff-109">If you plan to expose third-party COM types to other applications, always use the primary interop assembly provided by the same publisher as the type library it defines.</span></span> <span data-ttu-id="b20ff-110">Kromě zajištění kompatibility zaručenou typu, jsou často přizpůsobit primární spolupracující sestavení dodavatel zlepšení interakce.</span><span class="sxs-lookup"><span data-stu-id="b20ff-110">In addition to providing guaranteed type compatibility, primary interop assemblies are often customized by the vendor to enhance interoperability.</span></span>  
  
 <span data-ttu-id="b20ff-111">I v případě, že neplánujete vystavit typy modelu COM třetích stran, můžete pomocí primární spolupracující sestavení usnadňují úlohy vzájemné spolupráci se službou COM – součásti.</span><span class="sxs-lookup"><span data-stu-id="b20ff-111">Even if you do not plan to expose third-party COM types, using the primary interop assembly can ease the task of interoperating with COM components.</span></span> <span data-ttu-id="b20ff-112">Tato strategie však poskytuje žádná izolace z změny, které typy definované v primární spolupracující sestavení může provést dodavatele.</span><span class="sxs-lookup"><span data-stu-id="b20ff-112">However, this strategy provides no insulation from changes a vendor might make to types defined in a primary interop assembly.</span></span> <span data-ttu-id="b20ff-113">Pokud vaše aplikace vyžaduje tyto izolace, generovat vlastní sestavení vzájemné spolupráce místo použití primární spolupracující sestavení.</span><span class="sxs-lookup"><span data-stu-id="b20ff-113">When your application requires such insulation, generate your own interop assembly instead of using the primary interop assembly.</span></span>  
  
 <span data-ttu-id="b20ff-114">Je nutné zaregistrovat všechny získal primární spolupracující sestavení ve svém vývojovém počítači předtím, než můžete odkazovat pomocí [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b20ff-114">You must register all acquired primary interop assemblies on your development computer before you can reference them with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span></span> <span data-ttu-id="b20ff-115">Visual Studio vyhledává a používá primární spolupracující sestavení poprvé odkazovat na typ z knihovny typů COM.</span><span class="sxs-lookup"><span data-stu-id="b20ff-115">Visual Studio looks for and uses a primary interop assembly the first time that you reference a type from a COM type library.</span></span> <span data-ttu-id="b20ff-116">Pokud Visual Studio nemůže najít primární spolupracující sestavení přidružené ke knihovně typů, vás vyzve, abyste ho získat nebo nabízí místo vytvoření spolupráce sestavení.</span><span class="sxs-lookup"><span data-stu-id="b20ff-116">If Visual Studio cannot locate the primary interop assembly associated with the type library, it prompts you to acquire it or offers to create an interop assembly instead.</span></span> <span data-ttu-id="b20ff-117">Podobně [Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) také používá registru k vyhledání primární spolupracující sestavení.</span><span class="sxs-lookup"><span data-stu-id="b20ff-117">Likewise, the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) also uses the registry to locate primary interop assemblies.</span></span>  
  
 <span data-ttu-id="b20ff-118">Ačkoli to není potřeba registrace primárních sestavení spolupráce, pokud máte v úmyslu použít Visual Studio, poskytne mu nástroj registrace dvě výhody:</span><span class="sxs-lookup"><span data-stu-id="b20ff-118">Although it is not necessary to register primary interop assemblies unless you plan to use Visual Studio, registration provides two advantages:</span></span>  
  
-   <span data-ttu-id="b20ff-119">Registrovaný primární spolupracující sestavení je přehledně označen v klíči registru původní knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b20ff-119">A registered primary interop assembly is clearly marked under the registry key of the original type library.</span></span> <span data-ttu-id="b20ff-120">Registrace je nejlepší způsob vyhledejte primární spolupracující sestavení v počítači.</span><span class="sxs-lookup"><span data-stu-id="b20ff-120">Registration is the best way for you to locate a primary interop assembly on your computer.</span></span>  
  
-   <span data-ttu-id="b20ff-121">Omylem generování a použití nového sestavení vzájemné spolupráce, pokud někdy v budoucnu, pomocí sady Visual Studio odkazovat na typ, pro které máte registrace sestavení primární spolupráce se můžete vyhnout.</span><span class="sxs-lookup"><span data-stu-id="b20ff-121">You can avoid accidentally generating and using a new interop assembly if, at some time in the future, you do use Visual Studio to reference a type for which you have an unregistered primary interop assembly.</span></span>  
  
 <span data-ttu-id="b20ff-122">Použití [nástroj pro registraci sestavení (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) registrace primárních sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="b20ff-122">Use the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register a primary interop assembly.</span></span>  
  
### <a name="to-register-a-primary-interop-assembly"></a><span data-ttu-id="b20ff-123">Registrace primárních sestavení vzájemné spolupráce</span><span class="sxs-lookup"><span data-stu-id="b20ff-123">To register a primary interop assembly</span></span>  
  
1.  <span data-ttu-id="b20ff-124">V příkazovém řádku zadejte příkaz:</span><span class="sxs-lookup"><span data-stu-id="b20ff-124">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="b20ff-125">**modul RegAsm** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="b20ff-125">**regasm** *assemblyname*</span></span>  
  
     <span data-ttu-id="b20ff-126">V tomto příkazu *assemblyname* je název souboru sestavení, které je registrované.</span><span class="sxs-lookup"><span data-stu-id="b20ff-126">In this command, *assemblyname* is the file name of the assembly that is registered.</span></span> <span data-ttu-id="b20ff-127">RegAsm.exe přidá položku pro primární spolupracující sestavení v klíči registru jako původní knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b20ff-127">Regasm.exe adds an entry for the primary interop assembly under the same registry key as the original type library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b20ff-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="b20ff-128">Example</span></span>  
 <span data-ttu-id="b20ff-129">Zaregistruje v následujícím příkladu `CompanyA.UtilLib.dll` primární spolupracující sestavení.</span><span class="sxs-lookup"><span data-stu-id="b20ff-129">The following example registers the `CompanyA.UtilLib.dll` primary interop assembly.</span></span>  
  
```  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="b20ff-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b20ff-130">See Also</span></span>  
 [<span data-ttu-id="b20ff-131">Programování s primární spolupráce – sestavení</span><span class="sxs-lookup"><span data-stu-id="b20ff-131">Programming with Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)  
 [<span data-ttu-id="b20ff-132">Vyhledání primární spolupráce – sestavení</span><span class="sxs-lookup"><span data-stu-id="b20ff-132">Locating Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/d6768e4b-cd80-414d-a4f8-05d979eb393b)  
 [<span data-ttu-id="b20ff-133">Redistribuce primární spolupráce – sestavení</span><span class="sxs-lookup"><span data-stu-id="b20ff-133">Redistributing Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/e76384f0-d631-474c-bdbd-13884cba0265)
