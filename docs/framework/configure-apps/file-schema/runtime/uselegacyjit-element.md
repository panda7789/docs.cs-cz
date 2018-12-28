---
title: '&lt;useLegacyJit&gt; – Element'
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd4f9728338ecc66f84fe42b9bdbda9938ed518b
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612189"
---
# <a name="ltuselegacyjitgt-element"></a><span data-ttu-id="2266e-102">&lt;useLegacyJit&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="2266e-102">&lt;useLegacyJit&gt; Element</span></span>

<span data-ttu-id="2266e-103">Určuje, zda modul common language runtime používá starší verzi 64bitového kompilátoru JIT kompilace just-in-time.</span><span class="sxs-lookup"><span data-stu-id="2266e-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="2266e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2266e-104">\<configuration></span></span>  
<span data-ttu-id="2266e-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="2266e-105">\<runtime></span></span>  
<span data-ttu-id="2266e-106">\<useLegacyJit ></span><span class="sxs-lookup"><span data-stu-id="2266e-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="2266e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2266e-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="2266e-108">Název elementu `useLegacyJit` velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="2266e-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2266e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2266e-109">Attributes and elements</span></span>

<span data-ttu-id="2266e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2266e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2266e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2266e-111">Attributes</span></span>  
  
| <span data-ttu-id="2266e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2266e-112">Attribute</span></span> | <span data-ttu-id="2266e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2266e-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="2266e-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2266e-114">Required attribute.</span></span><br><br><span data-ttu-id="2266e-115">Určuje, zda modul runtime používá starší verzi 64bitového kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="2266e-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="2266e-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="2266e-116">enabled attribute</span></span>  
  
| <span data-ttu-id="2266e-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2266e-117">Value</span></span> | <span data-ttu-id="2266e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2266e-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="2266e-119">0</span><span class="sxs-lookup"><span data-stu-id="2266e-119">0</span></span>     | <span data-ttu-id="2266e-120">Modul common language runtime používá nový kompilátor JIT 64-bit zahrnuty v rozhraní .NET Framework 4.6 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="2266e-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="2266e-121">1</span><span class="sxs-lookup"><span data-stu-id="2266e-121">1</span></span>     | <span data-ttu-id="2266e-122">Modul common language runtime používá starší 64bitovým kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="2266e-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="2266e-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="2266e-123">Child elements</span></span>

<span data-ttu-id="2266e-124">Žádná</span><span class="sxs-lookup"><span data-stu-id="2266e-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="2266e-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="2266e-125">Parent elements</span></span>  
  
| <span data-ttu-id="2266e-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="2266e-126">Element</span></span>         | <span data-ttu-id="2266e-127">Popis</span><span class="sxs-lookup"><span data-stu-id="2266e-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="2266e-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2266e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="2266e-129">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2266e-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="2266e-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2266e-130">Remarks</span></span>  

<span data-ttu-id="2266e-131">Od verze rozhraní .NET Framework 4.6, modul common language runtime používá nový 64bitový kompilátor pro kompilaci za běhu (JIT) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2266e-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="2266e-132">V některých případech to může vést rozdíl v chování od kódu aplikace, který byl zkompilován JIT Kompilátorem v předchozí verzi 64bitového kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="2266e-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="2266e-133">Tím, že nastavíte `enabled` atribut `<useLegacyJit>` element `1`, můžete zakázat nového 64bitového kompilátoru JIT a místo toho zkompilujte aplikaci pomocí starší verze 64bitovým kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="2266e-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2266e-134">`<useLegacyJit>` Element ovlivňuje pouze kompilaci JIT 64-bit.</span><span class="sxs-lookup"><span data-stu-id="2266e-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="2266e-135">Kompilace s kompilátorem JIT 32 bitů je poškozena.</span><span class="sxs-lookup"><span data-stu-id="2266e-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="2266e-136">Namísto použití souboru nastavení konfigurace, můžete povolit starší verzi 64bitového kompilátoru JIT dvěma dalšími způsoby:</span><span class="sxs-lookup"><span data-stu-id="2266e-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="2266e-137">Nastavení proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="2266e-137">Setting an environment variable</span></span>

  <span data-ttu-id="2266e-138">Nastavte `COMPLUS_useLegacyJit` proměnnou prostředí, aby buď `0` (použití nového 64bitového kompilátoru JIT) nebo `1` (použijte starší 64bitového kompilátoru JIT):</span><span class="sxs-lookup"><span data-stu-id="2266e-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="2266e-139">Proměnná prostředí má *globálním rozsahem*, což znamená, že to má vliv na všechny aplikace, spusťte na počítači.</span><span class="sxs-lookup"><span data-stu-id="2266e-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="2266e-140">Pokud nastavit, je možné přepsat nastavení konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2266e-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="2266e-141">Název proměnné prostředí není malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2266e-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="2266e-142">Přidání klíče registru</span><span class="sxs-lookup"><span data-stu-id="2266e-142">Adding a registry key</span></span>

  <span data-ttu-id="2266e-143">Můžete povolit starší verzi 64bitového kompilátoru JIT tak, že přidáte `REG_DWORD` hodnota, která má buď `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` nebo `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče v registru.</span><span class="sxs-lookup"><span data-stu-id="2266e-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="2266e-144">Hodnota jmenuje `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="2266e-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="2266e-145">Pokud je hodnota 0, použije se nový kompilátor.</span><span class="sxs-lookup"><span data-stu-id="2266e-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="2266e-146">Pokud je hodnota 1, starší verzi 64bitového kompilátoru JIT je povolená.</span><span class="sxs-lookup"><span data-stu-id="2266e-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="2266e-147">Název hodnoty registru není malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2266e-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="2266e-148">Přidání hodnoty `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíč má vliv na všechny aplikace spuštěné na počítači.</span><span class="sxs-lookup"><span data-stu-id="2266e-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="2266e-149">Přidání hodnoty `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíč má vliv na všechny aplikace, které se spustí aktuální uživatel.</span><span class="sxs-lookup"><span data-stu-id="2266e-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="2266e-150">Pokud počítač je nakonfigurovaný s několika uživatelskými účty, ovlivníte jenom aplikace, které aktuální uživatel spouštět, pokud hodnota je přidána do klíče registru pro ostatní uživatele také.</span><span class="sxs-lookup"><span data-stu-id="2266e-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="2266e-151">Přidávání `<useLegacyJit>` prvku do konfiguračního souboru přepíše nastavení registru v případě, že jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2266e-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2266e-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="2266e-152">Example</span></span>  

<span data-ttu-id="2266e-153">Následující konfigurační soubor zakazuje kompilaci pomocí nového 64bitového kompilátoru JIT a místo toho používá starší verzi 64bitového kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="2266e-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2266e-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2266e-154">See also</span></span>

- [<span data-ttu-id="2266e-155">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="2266e-155">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)   
- [<span data-ttu-id="2266e-156">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="2266e-156">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)   
- [<span data-ttu-id="2266e-157">Omezení rizik: Nový kompilátor JIT 64-bit</span><span class="sxs-lookup"><span data-stu-id="2266e-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
