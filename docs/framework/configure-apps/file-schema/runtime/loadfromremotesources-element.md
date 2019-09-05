---
title: Element <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83980d315c83aa5cc23944dbd271c29e0ed83206
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252469"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="a0475-102">\<loadFromRemoteSources – element ></span><span class="sxs-lookup"><span data-stu-id="a0475-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="a0475-103">Určuje, zda mají být sestavení načtena ze vzdálených zdrojů udělena plná důvěryhodnost v .NET Framework 4 a novějších.</span><span class="sxs-lookup"><span data-stu-id="a0475-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a0475-104">Pokud jste byli přesměrováni na tento článek z důvodu chybové zprávy v seznamu chyb projektu sady Visual Studio nebo chyba sestavení, přečtěte [si téma How to: Použijte sestavení z webu v aplikaci Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a0475-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="a0475-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0475-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a0475-106">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0475-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a0475-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<loadFromRemoteSources >**</span><span class="sxs-lookup"><span data-stu-id="a0475-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0475-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0475-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0475-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0475-109">Attributes and elements</span></span>
 <span data-ttu-id="a0475-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a0475-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0475-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0475-111">Attributes</span></span>  
  
|<span data-ttu-id="a0475-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="a0475-112">Attribute</span></span>|<span data-ttu-id="a0475-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a0475-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a0475-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0475-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a0475-115">Určuje, jestli má být sestavení, které je načtené ze vzdáleného zdroje, udělené plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a0475-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a0475-116">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="a0475-116">enabled attribute</span></span>  
  
|<span data-ttu-id="a0475-117">Value</span><span class="sxs-lookup"><span data-stu-id="a0475-117">Value</span></span>|<span data-ttu-id="a0475-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a0475-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a0475-119">Neudělujete úplný vztah důvěryhodnosti aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="a0475-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="a0475-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a0475-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a0475-121">Udělte úplný vztah důvěryhodnosti aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="a0475-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0475-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a0475-122">Child elements</span></span>  
 <span data-ttu-id="a0475-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a0475-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0475-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="a0475-124">Parent elements</span></span>  
  
|<span data-ttu-id="a0475-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0475-125">Element</span></span>|<span data-ttu-id="a0475-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a0475-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a0475-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0475-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a0475-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a0475-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0475-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0475-129">Remarks</span></span>

<span data-ttu-id="a0475-130">Pokud se v .NET Framework 3,5 a starších verzích načte sestavení ze vzdáleného umístění, kód v sestavení běží v částečném vztahu důvěryhodnosti se sadou udělení, která závisí na zóně, ze které je načtena.</span><span class="sxs-lookup"><span data-stu-id="a0475-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="a0475-131">Například pokud načtete sestavení z webu, je načteno do zóny Internet a udělena sada oprávnění Internet.</span><span class="sxs-lookup"><span data-stu-id="a0475-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="a0475-132">Jinými slovy se spustí v internetovém prostoru.</span><span class="sxs-lookup"><span data-stu-id="a0475-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="a0475-133">Počínaje .NET Framework 4 jsou zásady zabezpečení přístupu kódu (CAS) zakázané a sestavení se načítají v úplném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a0475-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="a0475-134">Obvykle to udělí úplný vztah důvěryhodnosti k sestavením načteným pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody, která dříve byla izolovaného prostoru (sandbox).</span><span class="sxs-lookup"><span data-stu-id="a0475-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="a0475-135">Aby se zabránilo tomu, možnost spouštění kódu v sestaveních načtených ze vzdáleného zdroje je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="a0475-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="a0475-136">Ve výchozím nastavení platí, že pokud se pokusíte načíst vzdálené sestavení <xref:System.IO.FileLoadException> , bude vyvolána zpráva s výjimkou, například následující:</span><span class="sxs-lookup"><span data-stu-id="a0475-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="a0475-137">Chcete-li načíst sestavení a spustit jeho kód, je nutné buď:</span><span class="sxs-lookup"><span data-stu-id="a0475-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="a0475-138">Explicitní vytvoření izolovaného prostoru pro sestavení (viz [How to: Spustit částečně důvěryhodný kód v izolovaném](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)prostoru (sandbox)).</span><span class="sxs-lookup"><span data-stu-id="a0475-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="a0475-139">Spusťte kód sestavení v úplném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a0475-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="a0475-140">To provedete tak, `<loadFromRemoteSources>` že nakonfigurujete prvek.</span><span class="sxs-lookup"><span data-stu-id="a0475-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="a0475-141">Umožňuje určit, že sestavení, která běží v částečném vztahu důvěryhodnosti v dřívějších verzích .NET Framework nyní běží v úplném vztahu důvěryhodnosti v .NET Framework 4 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="a0475-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a0475-142">Pokud by sestavení nemělo běžet v úplném vztahu důvěryhodnosti, nenastavte tento prvek konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a0475-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="a0475-143">Místo toho vytvořte izolovaný prostor <xref:System.AppDomain> , ve kterém chcete sestavení načíst.</span><span class="sxs-lookup"><span data-stu-id="a0475-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="a0475-144">`enabled` Atribut`<loadFromRemoteSources>` pro element je platný pouze v případě, že je zakázáno zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="a0475-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="a0475-145">Ve výchozím nastavení jsou zásady CAS zakázané v .NET Framework 4 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="a0475-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="a0475-146">Pokud nastavíte `enabled` na `true`, jsou vzdálená sestavení udělena plná důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="a0475-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="a0475-147">Pokud `enabled` není nastaven na `true`, <xref:System.IO.FileLoadException> je vyvolána jedna z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="a0475-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="a0475-148">Chování izolovaného prostoru aktuální domény se liší od chování v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="a0475-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="a0475-149">To vyžaduje, aby byly zásady CAS zakázané a aby aktuální doména nebyla v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="a0475-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="a0475-150">Načtené sestavení není ze `MyComputer` zóny.</span><span class="sxs-lookup"><span data-stu-id="a0475-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="a0475-151">Nastavení elementu pro `true` zabránění vyvolání této výjimky. `<loadFromRemoteSources>`</span><span class="sxs-lookup"><span data-stu-id="a0475-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="a0475-152">Umožňuje určit, že se nespoléháte na modul CLR (Common Language Runtime) k izolovanému prostoru pro načtená sestavení pro zabezpečení a že může být povoleno provádět v úplném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a0475-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="a0475-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0475-153">Notes</span></span>

- <span data-ttu-id="a0475-154">V .NET Framework 4,5 a novějších verzích jsou sestavení v místních síťových sdílených složkách ve výchozím nastavení spouštěna v úplném vztahu důvěryhodnosti. není nutné povolit `<loadFromRemoteSources>` element.</span><span class="sxs-lookup"><span data-stu-id="a0475-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="a0475-155">Pokud byla aplikace zkopírována z webu, je označena systémem Windows jako webová aplikace, a to i v případě, že se nachází v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="a0475-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="a0475-156">Toto označení můžete změnit změnou jeho vlastností souboru, nebo můžete použít `<loadFromRemoteSources>` element pro udělení úplného vztahu důvěryhodnosti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0475-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="a0475-157">Alternativně můžete použít <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metodu pro načtení místního sestavení, které má operační systém označen jako načtený z webu.</span><span class="sxs-lookup"><span data-stu-id="a0475-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="a0475-158">Můžete se dostat <xref:System.IO.FileLoadException> do aplikace, která běží v aplikaci Virtual PC v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a0475-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="a0475-159">K tomu může dojít při pokusu o načtení souboru z propojených složek v hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="a0475-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="a0475-160">Může k tomu dojít i v případě, že se pokusíte načíst soubor ze složky propojené přes [službu Vzdálená plocha](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminálová služba).</span><span class="sxs-lookup"><span data-stu-id="a0475-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="a0475-161">Chcete-li výjimku zabránit, `enabled` nastavte `true`na.</span><span class="sxs-lookup"><span data-stu-id="a0475-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="a0475-162">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="a0475-162">Configuration file</span></span>

<span data-ttu-id="a0475-163">Tento element se obvykle používá v konfiguračním souboru aplikace, ale lze jej použít v jiných konfiguračních souborech v závislosti na kontextu.</span><span class="sxs-lookup"><span data-stu-id="a0475-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="a0475-164">Další informace najdete v článku [více implicitních použití zásad CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) na blogu zabezpečení .NET.</span><span class="sxs-lookup"><span data-stu-id="a0475-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="a0475-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0475-165">Example</span></span>

<span data-ttu-id="a0475-166">Následující příklad ukazuje, jak udělit úplný vztah důvěryhodnosti k sestavením načteným ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="a0475-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="a0475-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0475-167">See also</span></span>

- [<span data-ttu-id="a0475-168">Více implicitních použití zásad CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="a0475-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="a0475-169">Postupy: Spustit částečně důvěryhodný kód v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="a0475-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="a0475-170">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a0475-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a0475-171">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a0475-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
