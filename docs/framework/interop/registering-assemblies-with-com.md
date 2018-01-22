---
title: "Registrování sestav pomocí modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39466115e3835361c76361d3cfc04f76161e7dd5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="registering-assemblies-with-com"></a><span data-ttu-id="4830d-102">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="4830d-102">Registering Assemblies with COM</span></span>
<span data-ttu-id="4830d-103">Můžete spustit nástroj příkazového řádku volat [nástroj pro registraci sestavení (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) k registraci nebo zrušení registrace sestavení pro použití v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="4830d-103">You can run a command-line tool called the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register or unregister an assembly for use with COM.</span></span> <span data-ttu-id="4830d-104">RegAsm.exe informace o třídě přidá do registru systému, klienti COM můžete použít třídu rozhraní .NET Framework transparentně.</span><span class="sxs-lookup"><span data-stu-id="4830d-104">Regasm.exe adds information about the class to the system registry so COM clients can use the .NET Framework class transparently.</span></span> <span data-ttu-id="4830d-105"><xref:System.Runtime.InteropServices.RegistrationServices> Třída poskytuje ekvivalentní funkce.</span><span class="sxs-lookup"><span data-stu-id="4830d-105">The <xref:System.Runtime.InteropServices.RegistrationServices> class provides the equivalent functionality.</span></span>  
  
 <span data-ttu-id="4830d-106">Spravované součásti musí být zaregistrován v registru systému Windows, než je možné aktivovat z COM klienta.</span><span class="sxs-lookup"><span data-stu-id="4830d-106">A managed component must be registered in the Windows registry before it can be activated from a COM client.</span></span> <span data-ttu-id="4830d-107">V následující tabulce jsou uvedeny klíčů, které Regasm.exe obvykle přidá do registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4830d-107">The following table shows the keys that Regasm.exe typically adds to the Windows registry.</span></span> <span data-ttu-id="4830d-108">(000000 znamená skutečná hodnota GUID.)</span><span class="sxs-lookup"><span data-stu-id="4830d-108">(000000 indicates the actual GUID value.)</span></span>  
  
|<span data-ttu-id="4830d-109">GUID</span><span class="sxs-lookup"><span data-stu-id="4830d-109">GUID</span></span>|<span data-ttu-id="4830d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4830d-110">Description</span></span>|<span data-ttu-id="4830d-111">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="4830d-111">Registry key</span></span>|  
|----------|-----------------|------------------|  
|<span data-ttu-id="4830d-112">CLSID</span><span class="sxs-lookup"><span data-stu-id="4830d-112">CLSID</span></span>|<span data-ttu-id="4830d-113">Identifikátor třídy</span><span class="sxs-lookup"><span data-stu-id="4830d-113">Class identifier</span></span>|<span data-ttu-id="4830d-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="4830d-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span></span>|  
|<span data-ttu-id="4830d-115">IID</span><span class="sxs-lookup"><span data-stu-id="4830d-115">IID</span></span>|<span data-ttu-id="4830d-116">Identifikátor rozhraní</span><span class="sxs-lookup"><span data-stu-id="4830d-116">Interface identifier</span></span>|<span data-ttu-id="4830d-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="4830d-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span></span>|  
|<span data-ttu-id="4830d-118">LIBID</span><span class="sxs-lookup"><span data-stu-id="4830d-118">LIBID</span></span>|<span data-ttu-id="4830d-119">Identifikátor knihovny</span><span class="sxs-lookup"><span data-stu-id="4830d-119">Library identifier</span></span>|<span data-ttu-id="4830d-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="4830d-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span></span>|  
|<span data-ttu-id="4830d-121">ProgID</span><span class="sxs-lookup"><span data-stu-id="4830d-121">ProgID</span></span>|<span data-ttu-id="4830d-122">Programový identifikátor</span><span class="sxs-lookup"><span data-stu-id="4830d-122">Programmatic identifier</span></span>|<span data-ttu-id="4830d-123">HKEY_CLASSES_ROOT\000…000</span><span class="sxs-lookup"><span data-stu-id="4830d-123">HKEY_CLASSES_ROOT\000…000</span></span>|  
  
 <span data-ttu-id="4830d-124">V části HKCR\CLSID\\{0000... 0000} klíč, výchozí hodnota je nastavena na ProgID třídy a přidají dva nové pojmenovaných hodnot, třídy a sestavení.</span><span class="sxs-lookup"><span data-stu-id="4830d-124">Under the HKCR\CLSID\\{0000…0000} key, the default value is set to the ProgID of the class, and two new named values, Class and Assembly, are added.</span></span> <span data-ttu-id="4830d-125">Modul runtime čte hodnotu sestavení z registru a předá je do překladač sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="4830d-125">The runtime reads the Assembly value from the registry and passes it on to the runtime assembly resolver.</span></span> <span data-ttu-id="4830d-126">Překladač sestavení se pokusí najít sestavení, na základě informací o sestavení, jako je například číslo název a verze.</span><span class="sxs-lookup"><span data-stu-id="4830d-126">The assembly resolver attempts to locate the assembly, based on assembly information such as the name and version number.</span></span> <span data-ttu-id="4830d-127">Sestavení pro překladač sestavení, který se má najít sestavení, musí být v jednom z následujících umístění:</span><span class="sxs-lookup"><span data-stu-id="4830d-127">For the assembly resolver to locate an assembly, the assembly has to be in one of the following locations:</span></span>  
  
-   <span data-ttu-id="4830d-128">Globální mezipaměti sestavení (musí být sestavení se silným názvem).</span><span class="sxs-lookup"><span data-stu-id="4830d-128">The global assembly cache (must be a strong-named assembly).</span></span>  
  
-   <span data-ttu-id="4830d-129">V adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="4830d-129">In the application directory.</span></span> <span data-ttu-id="4830d-130">Sestavení ze cesta aplikace načíst jsou přístupné z této aplikace jenom.</span><span class="sxs-lookup"><span data-stu-id="4830d-130">Assemblies loaded from the application path are only accessible from that application.</span></span>  
  
-   <span data-ttu-id="4830d-131">Společně cesta k souboru zadaným **/ codebase** možnost Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="4830d-131">Along an file path specified with the **/codebase** option to Regasm.exe.</span></span>  
  
 <span data-ttu-id="4830d-132">RegAsm.exe také vytvoří klíč InProcServer32 pod HKCR\CLSID\\{0000... 0000} klíč.</span><span class="sxs-lookup"><span data-stu-id="4830d-132">Regasm.exe also creates the InProcServer32 key under the HKCR\CLSID\\{0000…0000} key.</span></span> <span data-ttu-id="4830d-133">Výchozí hodnota pro klíč nastavena na název knihovny DLL, která inicializuje modul common language runtime (Mscoree.dll).</span><span class="sxs-lookup"><span data-stu-id="4830d-133">The default value for the key is set to the name of the DLL that initializes the common language runtime (Mscoree.dll).</span></span>  
  
## <a name="examining-registry-entries"></a><span data-ttu-id="4830d-134">Ověření položky registru</span><span class="sxs-lookup"><span data-stu-id="4830d-134">Examining Registry Entries</span></span>  
 <span data-ttu-id="4830d-135">Zprostředkovatel komunikace s objekty COM poskytuje objekt pro vytváření implementaci standardní třídy pro vytvoření instance libovolné třídy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4830d-135">COM interop provides a standard class factory implementation to create an instance of any .NET Framework class.</span></span> <span data-ttu-id="4830d-136">Klienti mohou volat **DllGetClassObject** na spravovanou knihovnu DLL získat objekt pro vytváření tříd a vytvořit objekty, stejně jako jakoukoli jinou součástí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="4830d-136">Clients can call **DllGetClassObject** on the managed DLL to get a class factory and create objects, just as they would with any other COM component.</span></span>  
  
 <span data-ttu-id="4830d-137">Pro `InprocServer32` podklíč, zobrazí se odkaz na Mscoree.dll místo tradiční knihovny typů COM indikující, že modul common language runtime vytvoří spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="4830d-137">For the `InprocServer32` subkey, a reference to Mscoree.dll appears in place of a traditional COM type library to indicate that the common language runtime creates the managed object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4830d-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="4830d-138">See Also</span></span>  
 [<span data-ttu-id="4830d-139">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="4830d-139">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="4830d-140">Postupy: Odkazování na typy .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="4830d-140">How to: Reference .NET Types from COM</span></span>](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)  
 [<span data-ttu-id="4830d-141">Volání metody objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="4830d-141">Calling a .NET Object</span></span>](http://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [<span data-ttu-id="4830d-142">Nasazení aplikace pro přístup COM</span><span class="sxs-lookup"><span data-stu-id="4830d-142">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce)
