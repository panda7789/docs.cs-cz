---
title: Element <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a126b8c0050a8d1fd96a3d090f9b018a9faa07a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968859"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="7f4a6-102">Element \<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="7f4a6-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="7f4a6-103">Určuje, zda modul CLR (Common Language Runtime) používá starší 64 kompilátor JIT pro kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a><span data-ttu-id="7f4a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f4a6-104">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="7f4a6-105">V názvu elementu `useLegacyJit` se rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-105">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f4a6-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f4a6-106">Attributes and elements</span></span>

<span data-ttu-id="7f4a6-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f4a6-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f4a6-108">Attributes</span></span>  
  
| <span data-ttu-id="7f4a6-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f4a6-109">Attribute</span></span> | <span data-ttu-id="7f4a6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7f4a6-110">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="7f4a6-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-111">Required attribute.</span></span><br><br><span data-ttu-id="7f4a6-112">Určuje, zda modul runtime používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-112">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="7f4a6-113">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="7f4a6-113">enabled attribute</span></span>  
  
| <span data-ttu-id="7f4a6-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7f4a6-114">Value</span></span> | <span data-ttu-id="7f4a6-115">Description</span><span class="sxs-lookup"><span data-stu-id="7f4a6-115">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="7f4a6-116">0</span><span class="sxs-lookup"><span data-stu-id="7f4a6-116">0</span></span>     | <span data-ttu-id="7f4a6-117">Modul CLR (Common Language Runtime) používá nový 64 kompilátor JIT zahrnutý v .NET Framework 4,6 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-117">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="7f4a6-118">1</span><span class="sxs-lookup"><span data-stu-id="7f4a6-118">1</span></span>     | <span data-ttu-id="7f4a6-119">Modul common language runtime používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-119">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="7f4a6-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="7f4a6-120">Child elements</span></span>

<span data-ttu-id="7f4a6-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f4a6-121">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="7f4a6-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="7f4a6-122">Parent elements</span></span>  
  
| <span data-ttu-id="7f4a6-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f4a6-123">Element</span></span>         | <span data-ttu-id="7f4a6-124">Description</span><span class="sxs-lookup"><span data-stu-id="7f4a6-124">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="7f4a6-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="7f4a6-126">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-126">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="7f4a6-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f4a6-127">Remarks</span></span>  

<span data-ttu-id="7f4a6-128">Počínaje .NET Framework 4,6 používá modul CLR (Common Language Runtime) nový 64 kompilátor pro kompilaci JIT (just-in-time) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-128">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="7f4a6-129">V některých případech to může vést k rozdílu v chování z kódu aplikace, který byl zkompilován JIT pomocí předchozí verze 64 kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-129">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="7f4a6-130">Nastavením `enabled` atributu `<useLegacyJit>` elementu na `1` můžete zakázat nový 64 kompilátor JIT a místo toho zkompilovat aplikaci pomocí starší verze 64 kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-130">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f4a6-131">`<useLegacyJit>`Element ovlivňuje pouze 64 KOMPILACI JIT.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-131">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="7f4a6-132">Kompilace s 32 kompilátorem JIT není nijak ovlivněna.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-132">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="7f4a6-133">Namísto použití nastavení konfiguračního souboru můžete povolit starší 64 kompilátor JIT dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="7f4a6-133">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="7f4a6-134">Nastavení proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="7f4a6-134">Setting an environment variable</span></span>

  <span data-ttu-id="7f4a6-135">Nastavte `COMPLUS_useLegacyJit` proměnnou prostředí na buď `0` (použijte nový 64 kompilátor JIT), nebo `1` (použijte starší 64 kompilátor JIT):</span><span class="sxs-lookup"><span data-stu-id="7f4a6-135">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="7f4a6-136">Proměnná prostředí má *globální rozsah*, což znamená, že má vliv na všechny aplikace spuštěné v počítači.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-136">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="7f4a6-137">Pokud je tato hodnota nastavena, může být přepsána nastavením konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-137">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="7f4a6-138">V názvu proměnné prostředí se nerozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-138">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="7f4a6-139">Přidání klíče registru</span><span class="sxs-lookup"><span data-stu-id="7f4a6-139">Adding a registry key</span></span>

  <span data-ttu-id="7f4a6-140">Můžete povolit starší 64 kompilátor JIT přidáním `REG_DWORD` hodnoty do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče nebo v registru.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-140">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="7f4a6-141">Hodnota je pojmenována `useLegacyJit` .</span><span class="sxs-lookup"><span data-stu-id="7f4a6-141">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="7f4a6-142">Je-li hodnota 0, je použit nový kompilátor.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-142">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="7f4a6-143">Pokud je hodnota 1, je povolen starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-143">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="7f4a6-144">V názvu hodnoty registru se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-144">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="7f4a6-145">Přidání hodnoty do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíče má vliv na všechny aplikace spuštěné v počítači.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-145">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="7f4a6-146">Přidání hodnoty do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče má vliv na všechny aplikace spuštěné aktuálním uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-146">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="7f4a6-147">Pokud je počítač nakonfigurovaný s několika uživatelskými účty, ovlivní se jenom aplikace spuštěné aktuálním uživatelem, pokud se hodnota nepřidá do klíčů registru pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-147">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="7f4a6-148">Přidání `<useLegacyJit>` elementu do konfiguračního souboru přepíše nastavení registru, pokud jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-148">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f4a6-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f4a6-149">Example</span></span>  

<span data-ttu-id="7f4a6-150">Následující konfigurační soubor zakáže kompilaci s novým 64 kompilátorem JIT a místo toho používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="7f4a6-150">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f4a6-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f4a6-151">See also</span></span>

- [<span data-ttu-id="7f4a6-152">\<runtime>Objekt</span><span class="sxs-lookup"><span data-stu-id="7f4a6-152">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="7f4a6-153">\<configuration>Objekt</span><span class="sxs-lookup"><span data-stu-id="7f4a6-153">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="7f4a6-154">Zmírnění: nový 64 kompilátor JIT</span><span class="sxs-lookup"><span data-stu-id="7f4a6-154">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
