---
title: Element <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: 47aacb629dc234d9aeaab1ef6e6844fbbe5dbfdb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115111"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="64ce5-102">\<element > useLegacyJit</span><span class="sxs-lookup"><span data-stu-id="64ce5-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="64ce5-103">Určuje, zda modul CLR (Common Language Runtime) používá starší 64 kompilátor JIT pro kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="64ce5-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="64ce5-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="64ce5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="64ce5-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="64ce5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="64ce5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<useLegacyJit >**</span><span class="sxs-lookup"><span data-stu-id="64ce5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ce5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64ce5-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="64ce5-108">Název elementu `useLegacyJit` rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="64ce5-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64ce5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="64ce5-109">Attributes and elements</span></span>

<span data-ttu-id="64ce5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="64ce5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64ce5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="64ce5-111">Attributes</span></span>  
  
| <span data-ttu-id="64ce5-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="64ce5-112">Attribute</span></span> | <span data-ttu-id="64ce5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="64ce5-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="64ce5-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="64ce5-114">Required attribute.</span></span><br><br><span data-ttu-id="64ce5-115">Určuje, zda modul runtime používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="64ce5-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="64ce5-116">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="64ce5-116">enabled attribute</span></span>  
  
| <span data-ttu-id="64ce5-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="64ce5-117">Value</span></span> | <span data-ttu-id="64ce5-118">Popis</span><span class="sxs-lookup"><span data-stu-id="64ce5-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="64ce5-119">0,8</span><span class="sxs-lookup"><span data-stu-id="64ce5-119">0</span></span>     | <span data-ttu-id="64ce5-120">Modul CLR (Common Language Runtime) používá nový 64 kompilátor JIT zahrnutý v .NET Framework 4,6 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="64ce5-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="64ce5-121">první</span><span class="sxs-lookup"><span data-stu-id="64ce5-121">1</span></span>     | <span data-ttu-id="64ce5-122">Modul common language runtime používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="64ce5-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="64ce5-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="64ce5-123">Child elements</span></span>

<span data-ttu-id="64ce5-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="64ce5-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="64ce5-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="64ce5-125">Parent elements</span></span>  
  
| <span data-ttu-id="64ce5-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="64ce5-126">Element</span></span>         | <span data-ttu-id="64ce5-127">Popis</span><span class="sxs-lookup"><span data-stu-id="64ce5-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="64ce5-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="64ce5-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="64ce5-129">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="64ce5-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="64ce5-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64ce5-130">Remarks</span></span>  

<span data-ttu-id="64ce5-131">Počínaje .NET Framework 4,6 používá modul CLR (Common Language Runtime) nový 64 kompilátor pro kompilaci JIT (just-in-time) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="64ce5-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="64ce5-132">V některých případech to může vést k rozdílu v chování z kódu aplikace, který byl zkompilován JIT pomocí předchozí verze 64 kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="64ce5-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="64ce5-133">Nastavením atributu `enabled` elementu `<useLegacyJit>` na `1`můžete zakázat nový 64 kompilátor JIT a místo toho zkompilovat aplikaci pomocí staršího 64 kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="64ce5-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64ce5-134">Element `<useLegacyJit>` ovlivňuje pouze 64 kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="64ce5-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="64ce5-135">Kompilace s 32 kompilátorem JIT není nijak ovlivněna.</span><span class="sxs-lookup"><span data-stu-id="64ce5-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="64ce5-136">Namísto použití nastavení konfiguračního souboru můžete povolit starší 64 kompilátor JIT dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="64ce5-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="64ce5-137">Nastavení proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="64ce5-137">Setting an environment variable</span></span>

  <span data-ttu-id="64ce5-138">Nastavte proměnnou prostředí `COMPLUS_useLegacyJit` buď na `0` (použijte nový 64 kompilátor JIT), nebo `1` (použijte starší 64 kompilátor JIT):</span><span class="sxs-lookup"><span data-stu-id="64ce5-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="64ce5-139">Proměnná prostředí má *globální rozsah*, což znamená, že má vliv na všechny aplikace spuštěné v počítači.</span><span class="sxs-lookup"><span data-stu-id="64ce5-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="64ce5-140">Pokud je tato hodnota nastavena, může být přepsána nastavením konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="64ce5-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="64ce5-141">V názvu proměnné prostředí se nerozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="64ce5-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="64ce5-142">Přidání klíče registru</span><span class="sxs-lookup"><span data-stu-id="64ce5-142">Adding a registry key</span></span>

  <span data-ttu-id="64ce5-143">Můžete povolit starší 64 kompilátor JIT přidáním `REG_DWORD` hodnoty do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` nebo `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče v registru.</span><span class="sxs-lookup"><span data-stu-id="64ce5-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="64ce5-144">Hodnota je pojmenována `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="64ce5-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="64ce5-145">Je-li hodnota 0, je použit nový kompilátor.</span><span class="sxs-lookup"><span data-stu-id="64ce5-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="64ce5-146">Pokud je hodnota 1, je povolen starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="64ce5-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="64ce5-147">V názvu hodnoty registru se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="64ce5-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="64ce5-148">Přidání hodnoty do klíče `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` má vliv na všechny aplikace spuštěné v počítači.</span><span class="sxs-lookup"><span data-stu-id="64ce5-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="64ce5-149">Přidání hodnoty do klíče `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` má vliv na všechny aplikace spuštěné aktuálním uživatelem.</span><span class="sxs-lookup"><span data-stu-id="64ce5-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="64ce5-150">Pokud je počítač nakonfigurovaný s několika uživatelskými účty, ovlivní se jenom aplikace spuštěné aktuálním uživatelem, pokud se hodnota nepřidá do klíčů registru pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="64ce5-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="64ce5-151">Přidání prvku `<useLegacyJit>` do konfiguračního souboru přepíše nastavení registru, pokud jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="64ce5-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ce5-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="64ce5-152">Example</span></span>  

<span data-ttu-id="64ce5-153">Následující konfigurační soubor zakáže kompilaci s novým 64 kompilátorem JIT a místo toho používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="64ce5-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64ce5-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64ce5-154">See also</span></span>

- [<span data-ttu-id="64ce5-155">\<element > runtime</span><span class="sxs-lookup"><span data-stu-id="64ce5-155">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="64ce5-156">> element konfigurace \<</span><span class="sxs-lookup"><span data-stu-id="64ce5-156">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="64ce5-157">Zmírnění: nový 64 kompilátor JIT</span><span class="sxs-lookup"><span data-stu-id="64ce5-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
