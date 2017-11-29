---
title: "&lt;useLegacyJit&gt; – Element"
ms.custom: 
ms.date: 04/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 735733fc33a21c2f275c1ea9894c43558f01626e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltuselegacyjitgt-element"></a><span data-ttu-id="6875a-102">&lt;useLegacyJit&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="6875a-102">&lt;useLegacyJit&gt; Element</span></span>

<span data-ttu-id="6875a-103">Určuje, zda modul common language runtime používá starší verze 64bitový kompilátor JIT pro kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="6875a-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="6875a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="6875a-104">\<configuration></span></span>  
<span data-ttu-id="6875a-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="6875a-105">\<runtime></span></span>  
<span data-ttu-id="6875a-106">\<useLegacyJit ></span><span class="sxs-lookup"><span data-stu-id="6875a-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="6875a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6875a-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="6875a-108">Název elementu `useLegacyJit` je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6875a-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6875a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6875a-109">Attributes and elements</span></span>

<span data-ttu-id="6875a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6875a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6875a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6875a-111">Attributes</span></span>  
  
| <span data-ttu-id="6875a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6875a-112">Attribute</span></span> | <span data-ttu-id="6875a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6875a-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="6875a-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6875a-114">Required attribute.</span></span><br><br><span data-ttu-id="6875a-115">Určuje, zda modul runtime používá starší verze 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="6875a-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="6875a-116">povoleno atribut</span><span class="sxs-lookup"><span data-stu-id="6875a-116">enabled attribute</span></span>  
  
| <span data-ttu-id="6875a-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6875a-117">Value</span></span> | <span data-ttu-id="6875a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6875a-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="6875a-119">0</span><span class="sxs-lookup"><span data-stu-id="6875a-119">0</span></span>     | <span data-ttu-id="6875a-120">Modul CLR používá nové 64bitový JIT kompilátor zahrnuté v rozhraní .NET Framework 4.6 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="6875a-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="6875a-121">1</span><span class="sxs-lookup"><span data-stu-id="6875a-121">1</span></span>     | <span data-ttu-id="6875a-122">Modul CLR používá starší 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="6875a-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="6875a-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6875a-123">Child elements</span></span>

<span data-ttu-id="6875a-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="6875a-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="6875a-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6875a-125">Parent elements</span></span>  
  
| <span data-ttu-id="6875a-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="6875a-126">Element</span></span>         | <span data-ttu-id="6875a-127">Popis</span><span class="sxs-lookup"><span data-stu-id="6875a-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="6875a-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6875a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="6875a-129">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6875a-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="6875a-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6875a-130">Remarks</span></span>  

<span data-ttu-id="6875a-131">Od verze rozhraní .NET Framework 4.6, modul common language runtime používá nové 64bitový kompilátor pro kompilaci JIT (JIT) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6875a-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="6875a-132">V některých případech může výsledkem rozdíl v chování z aplikační kód, který byl kompilována předchozí verze 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="6875a-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="6875a-133">Nastavením `enabled` atribut `<useLegacyJit>` element `1`, můžete zakázat nové 64bitový kompilátor JIT a místo toho zkompilovat vaší aplikace pomocí starší verze 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="6875a-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6875a-134">`<useLegacyJit>` Element ovlivňuje pouze 64-bit JIT kompilace.</span><span class="sxs-lookup"><span data-stu-id="6875a-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="6875a-135">Kompilace pomocí JIT kompilátoru 32-bit je poškozena.</span><span class="sxs-lookup"><span data-stu-id="6875a-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="6875a-136">Místo použití souboru nastavení konfigurace, můžete povolit starší verze 64bitový kompilátor JIT dva další způsoby:</span><span class="sxs-lookup"><span data-stu-id="6875a-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="6875a-137">Nastavení proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="6875a-137">Setting an environment variable</span></span>

  <span data-ttu-id="6875a-138">Nastavte `COMPLUS_useLegacyJit` proměnnou prostředí buď `0` (použít nové 64bitový kompilátor JIT) nebo `1` (použijte starší 64bitový kompilátor JIT):</span><span class="sxs-lookup"><span data-stu-id="6875a-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="6875a-139">Proměnné prostředí má *globální obor*, což znamená, že ovlivňuje všechny aplikace spustit na počítači.</span><span class="sxs-lookup"><span data-stu-id="6875a-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="6875a-140">Pokud nastavíte, ho bude možné přepsat pomocí souboru nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="6875a-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="6875a-141">Název proměnné prostředí není malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6875a-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="6875a-142">Přidání klíče registru</span><span class="sxs-lookup"><span data-stu-id="6875a-142">Adding a registry key</span></span>

  <span data-ttu-id="6875a-143">Můžete povolit starší verze 64bitový kompilátor JIT přidáním `REG_DWORD` hodnota, která má buď `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` nebo `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče v registru.</span><span class="sxs-lookup"><span data-stu-id="6875a-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="6875a-144">Hodnota jmenuje `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="6875a-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="6875a-145">Pokud je hodnota 0, se používá nový kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6875a-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="6875a-146">Pokud je hodnota 1, je starší verze 64bitový kompilátor JIT povoleno.</span><span class="sxs-lookup"><span data-stu-id="6875a-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="6875a-147">Název hodnoty registru není malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6875a-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="6875a-148">Přidáním hodnoty do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíč ovlivní všechny aplikace spuštěné na počítači.</span><span class="sxs-lookup"><span data-stu-id="6875a-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="6875a-149">Přidáním hodnoty do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíč ovlivní všechny aplikace spouštěné aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="6875a-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="6875a-150">Pokud je počítač nakonfigurovaný s několika uživatelskými účty, jsou jenom aplikace, které spustí aktuální uživatel vliv, pokud hodnota klíče registru pro ostatní uživatele i.</span><span class="sxs-lookup"><span data-stu-id="6875a-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="6875a-151">Přidávání `<useLegacyJit>` element konfiguračního souboru přepíše nastavení registru, pokud jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6875a-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6875a-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="6875a-152">Example</span></span>  

<span data-ttu-id="6875a-153">Následující konfigurační soubor zakáže kompilaci s novou 64bitový kompilátor JIT a místo toho používá starší verze 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="6875a-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6875a-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="6875a-154">See also</span></span>

<span data-ttu-id="6875a-155">[\<modul runtime > elementu](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="6875a-155">[\<runtime> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span></span>  
<span data-ttu-id="6875a-156">[\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6875a-156">[\<configuration> Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
[<span data-ttu-id="6875a-157">Omezení rizik: Nové 64-bit JIT kompilátoru</span><span class="sxs-lookup"><span data-stu-id="6875a-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
