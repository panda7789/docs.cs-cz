---
title: Element <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154059"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="20b6d-102">\<loadFromRemoteSources> element</span><span class="sxs-lookup"><span data-stu-id="20b6d-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="20b6d-103">Určuje, zda mají být sestavením načteným ze vzdálených zdrojů udělena úplná důvěryhodnost v rozhraní .NET Framework 4 a novějších.</span><span class="sxs-lookup"><span data-stu-id="20b6d-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="20b6d-104">Pokud jste byli přesměrováni na tento článek z důvodu chybové zprávy v seznamu chyb projektu sady Visual Studio nebo chyby sestavení, [přečtěte si téma Postup: Použití sestavení z webu v sadě Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="20b6d-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="20b6d-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="20b6d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="20b6d-106">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="20b6d-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="20b6d-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span><span class="sxs-lookup"><span data-stu-id="20b6d-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b6d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20b6d-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20b6d-109">Atributy a prvky</span><span class="sxs-lookup"><span data-stu-id="20b6d-109">Attributes and elements</span></span>
 <span data-ttu-id="20b6d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="20b6d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20b6d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="20b6d-111">Attributes</span></span>  
  
|<span data-ttu-id="20b6d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="20b6d-112">Attribute</span></span>|<span data-ttu-id="20b6d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="20b6d-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="20b6d-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="20b6d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="20b6d-115">Určuje, zda má být sestavení načtené ze vzdáleného zdroje udělenúplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="20b6d-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="20b6d-116">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="20b6d-116">enabled attribute</span></span>  
  
|<span data-ttu-id="20b6d-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="20b6d-117">Value</span></span>|<span data-ttu-id="20b6d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="20b6d-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="20b6d-119">Neudělujte úplný vztah důvěryhodnosti aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="20b6d-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="20b6d-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="20b6d-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="20b6d-121">Udělte plnou důvěryhodnost aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="20b6d-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20b6d-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="20b6d-122">Child elements</span></span>  
 <span data-ttu-id="20b6d-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="20b6d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20b6d-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="20b6d-124">Parent elements</span></span>  
  
|<span data-ttu-id="20b6d-125">Element</span><span class="sxs-lookup"><span data-stu-id="20b6d-125">Element</span></span>|<span data-ttu-id="20b6d-126">Popis</span><span class="sxs-lookup"><span data-stu-id="20b6d-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="20b6d-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20b6d-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="20b6d-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="20b6d-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20b6d-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20b6d-129">Remarks</span></span>

<span data-ttu-id="20b6d-130">V rozhraní .NET Framework 3.5 a starších verzích pokud načtete sestavení ze vzdáleného umístění, kód v sestavení běží v částečném vztahu důvěryhodnosti s grantovou sadou, která závisí na zóně, ze které je načteno.</span><span class="sxs-lookup"><span data-stu-id="20b6d-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="20b6d-131">Pokud například načtete sestavení z webu, načte se do zóny Internet a bude mu udělena sada oprávnění k Internetu.</span><span class="sxs-lookup"><span data-stu-id="20b6d-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="20b6d-132">Jinými slovy, provádí se v internetové izolované masivu.</span><span class="sxs-lookup"><span data-stu-id="20b6d-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="20b6d-133">Počínaje rozhraním .NET Framework 4 je zakázána zásada zabezpečení přístupu kódu (CAS) a sestavení jsou načtena v plném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="20b6d-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="20b6d-134">Obvykle by to udělit úplný vztah důvěryhodnosti sestavení naložené <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> s metodou, která byla dříve v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="20b6d-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="20b6d-135">Chcete-li tomu zabránit, je ve výchozím nastavení zakázána možnost spouštět kód v sestaveních načtených ze vzdáleného zdroje.</span><span class="sxs-lookup"><span data-stu-id="20b6d-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="20b6d-136">Ve výchozím nastavení, pokud se pokusíte <xref:System.IO.FileLoadException> načíst vzdálené sestavení, a s výjimkou zprávy, jako je následující je vyvolána:</span><span class="sxs-lookup"><span data-stu-id="20b6d-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

<span data-ttu-id="20b6d-137">Chcete-li načíst sestavení a spustit jeho kód, musíte buď:</span><span class="sxs-lookup"><span data-stu-id="20b6d-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="20b6d-138">Explicitně vytvořte izolovaného prostoru pro sestavení (viz [Postup: Spustit částečně důvěryhodný kód v izolovaném prostoru).](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)</span><span class="sxs-lookup"><span data-stu-id="20b6d-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="20b6d-139">Spusťte kód sestavení v plném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="20b6d-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="20b6d-140">To provést konfigurací `<loadFromRemoteSources>` prvku.</span><span class="sxs-lookup"><span data-stu-id="20b6d-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="20b6d-141">Umožňuje určit, že sestavení, která jsou spuštěna v částečném vztahu důvěryhodnosti v dřívějších verzích rozhraní .NET Framework, jsou nyní spuštěna v plně důvěře v rozhraní .NET Framework 4 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="20b6d-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20b6d-142">Pokud by sestavení nemělo být spuštěno v plném vztahu důvěryhodnosti, nenastavujte tento konfigurační prvek.</span><span class="sxs-lookup"><span data-stu-id="20b6d-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="20b6d-143">Místo toho vytvořte sandbox, <xref:System.AppDomain> ve kterém chcete načíst sestavu.</span><span class="sxs-lookup"><span data-stu-id="20b6d-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="20b6d-144">Atribut `enabled` pro `<loadFromRemoteSources>` prvek je účinný pouze v případě, že je zakázáno zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="20b6d-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="20b6d-145">Ve výchozím nastavení je zásada CAS zakázána v rozhraní .NET Framework 4 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="20b6d-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="20b6d-146">Pokud nastavíte na `enabled` `true`, vzdálená sestavení jsou udělena plná důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="20b6d-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="20b6d-147">Není-li `enabled` nastavena na `true`, <xref:System.IO.FileLoadException> je a vyvolána za jedné z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="20b6d-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="20b6d-148">Chování sandboxing aktuální domény se liší od jeho chování v rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="20b6d-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="20b6d-149">To vyžaduje, aby byly zásady CAS zakázány a aktuální doména nebyla v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="20b6d-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="20b6d-150">Načtená sestava není ze `MyComputer` zóny.</span><span class="sxs-lookup"><span data-stu-id="20b6d-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="20b6d-151">Nastavení `<loadFromRemoteSources>` prvku `true` zabránit této výjimce vyvolána.</span><span class="sxs-lookup"><span data-stu-id="20b6d-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="20b6d-152">Umožňuje určit, že nespoléháte na běžný jazyk runtime do izolovaného prostoru načtená sestavení pro zabezpečení a že mohou být povoleny pro spuštění v plném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="20b6d-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="20b6d-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20b6d-153">Notes</span></span>

- <span data-ttu-id="20b6d-154">V rozhraní .NET Framework 4.5 a novějších verzích jsou sestavení sdílených složek místní sítě ve výchozím nastavení plně důvěryhodná. není třeba povolit `<loadFromRemoteSources>` prvek.</span><span class="sxs-lookup"><span data-stu-id="20b6d-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="20b6d-155">Pokud byla aplikace zkopírována z webu, je systémem Windows označena jako webová aplikace, i když je umístěna v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="20b6d-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="20b6d-156">Toto označení můžete změnit změnou jeho vlastností `<loadFromRemoteSources>` souboru nebo můžete prvek použít k udělení úplnédůvěryhodnosti sestavení.</span><span class="sxs-lookup"><span data-stu-id="20b6d-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="20b6d-157">Alternativně můžete použít metodu <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> k načtení místního sestavení, které operační systém označil jako načtené z webu.</span><span class="sxs-lookup"><span data-stu-id="20b6d-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="20b6d-158">Můžete získat <xref:System.IO.FileLoadException> v aplikaci, která je spuštěna v aplikaci Virtuální počítač se systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="20b6d-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="20b6d-159">K tomu může dojít při pokusu o načtení souboru z propojených složek v hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="20b6d-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="20b6d-160">Může k tomu dojít také při pokusu o načtení souboru ze složky propojené [prostředpou Vzdálená plocha](/windows/win32/termserv/terminal-services-portal) (Terminálová služba).</span><span class="sxs-lookup"><span data-stu-id="20b6d-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="20b6d-161">Chcete-li se `enabled` vyhnout `true`výjimce, nastavte na .</span><span class="sxs-lookup"><span data-stu-id="20b6d-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="20b6d-162">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="20b6d-162">Configuration file</span></span>

<span data-ttu-id="20b6d-163">Tento prvek se obvykle používá v konfiguračním souboru aplikace, ale lze jej použít v jiných konfiguračních souborech v závislosti na kontextu.</span><span class="sxs-lookup"><span data-stu-id="20b6d-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="20b6d-164">Další informace naleznete v článku [Další implicitní použití zásad CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) v blogu .NET Security.</span><span class="sxs-lookup"><span data-stu-id="20b6d-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="20b6d-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="20b6d-165">Example</span></span>

<span data-ttu-id="20b6d-166">Následující příklad ukazuje, jak udělit úplný vztah důvěryhodnosti sestavením načteným ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="20b6d-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="20b6d-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="20b6d-167">See also</span></span>

- [<span data-ttu-id="20b6d-168">Další implicitní použití zásad CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="20b6d-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="20b6d-169">Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="20b6d-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="20b6d-170">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="20b6d-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="20b6d-171">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="20b6d-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
