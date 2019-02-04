---
title: Element <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568129f30267b212737ec8aa688cf882e19bbff
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675306"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="b19d0-102">\<loadFromRemoteSources > – element</span><span class="sxs-lookup"><span data-stu-id="b19d0-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="b19d0-103">Určuje, zda sestavení načtená ze vzdáleného zdroje by měly být udělena úplná důvěryhodnost v rozhraní .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b19d0-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="b19d0-104">Pokud k tomuto článku byli přesměrováni z důvodu chybovou zprávu v seznamu chyb sady Visual Studio projekt nebo sestavení chyby, přečtěte si téma [jak: Použít sestavení z webu v sadě Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b19d0-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
 <span data-ttu-id="b19d0-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="b19d0-105">\<configuration></span></span>  
<span data-ttu-id="b19d0-106">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="b19d0-106">\<runtime></span></span>  
<span data-ttu-id="b19d0-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="b19d0-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19d0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b19d0-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b19d0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b19d0-109">Attributes and elements</span></span>
 <span data-ttu-id="b19d0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b19d0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b19d0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b19d0-111">Attributes</span></span>  
  
|<span data-ttu-id="b19d0-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b19d0-112">Attribute</span></span>|<span data-ttu-id="b19d0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b19d0-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b19d0-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b19d0-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b19d0-115">Určuje, zda sestavení, který je načten ze vzdáleného zdroje by měly být udělena úplná důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="b19d0-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b19d0-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="b19d0-116">enabled attribute</span></span>  
  
|<span data-ttu-id="b19d0-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b19d0-117">Value</span></span>|<span data-ttu-id="b19d0-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b19d0-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b19d0-119">Neudělujte úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="b19d0-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="b19d0-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b19d0-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b19d0-121">Udělte úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="b19d0-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b19d0-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b19d0-122">Child elements</span></span>  
 <span data-ttu-id="b19d0-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="b19d0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b19d0-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="b19d0-124">Parent elements</span></span>  
  
|<span data-ttu-id="b19d0-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="b19d0-125">Element</span></span>|<span data-ttu-id="b19d0-126">Popis</span><span class="sxs-lookup"><span data-stu-id="b19d0-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b19d0-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b19d0-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b19d0-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b19d0-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b19d0-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b19d0-129">Remarks</span></span>

<span data-ttu-id="b19d0-130">V rozhraní .NET Framework 3.5 a starší verze Pokud načtete sestavení ze vzdáleného umístění, spustí kód v sestavení v částečném vztahu důvěryhodnosti pomocí sady udělení, který závisí na zónu, ze které je načten.</span><span class="sxs-lookup"><span data-stu-id="b19d0-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="b19d0-131">Například pokud načtete sestavení z webu, je načten do zóny Internet a udělená sada oprávnění Internetu.</span><span class="sxs-lookup"><span data-stu-id="b19d0-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="b19d0-132">Jinými slovy spouští v sandboxu sítě Internet.</span><span class="sxs-lookup"><span data-stu-id="b19d0-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="b19d0-133">Od verze rozhraní .NET Framework 4, code access security (CAS) zásada je zakázána a sestavení jsou načtena v režimu plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="b19d0-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="b19d0-134">Obvykle to udělit úplný vztah důvěryhodnosti k sestavení načtená <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu, která dříve byla v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="b19d0-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="b19d0-135">Chcete-li tomu zabránit, umožňuje spouštění kódu v sestavení načtená ze vzdáleného zdroje je standardně zakázáno.</span><span class="sxs-lookup"><span data-stu-id="b19d0-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="b19d0-136">Ve výchozím nastavení, pokud se pokusíte načíst vzdálené sestavení <xref:System.IO.FileLoadException> se zprávou výjimky, jako je vyvolána následující výjimka:</span><span class="sxs-lookup"><span data-stu-id="b19d0-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="b19d0-137">Načtení sestavení a provedení jeho kód, musíte buď:</span><span class="sxs-lookup"><span data-stu-id="b19d0-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="b19d0-138">Explicitně vytvořit izolovaný prostor pro sestavení (viz [jak: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span><span class="sxs-lookup"><span data-stu-id="b19d0-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="b19d0-139">Spusťte sestavení kódu v režimu plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="b19d0-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="b19d0-140">To provedete tím, že nakonfigurujete `<loadFromRemoteSources>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b19d0-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="b19d0-141">To vám umožní zadat, že sestavení, na kterých běží v částečném vztahu důvěryhodnosti v dřívějších verzích rozhraní .NET Framework nyní spustit v úplném vztahu důvěryhodnosti v rozhraní .NET Framework 4 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="b19d0-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b19d0-142">Pokud sestavení by neměl spustit v úplném vztahu důvěryhodnosti, nenastavujte tento prvek konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b19d0-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="b19d0-143">Místo toho vytvořte v izolovaném prostoru <xref:System.AppDomain> ve kterých se mají načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="b19d0-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="b19d0-144">`enabled` Atribut pro `<loadFromRemoteSources>` element je účinné pouze když je zakázáno zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="b19d0-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="b19d0-145">Ve výchozím nastavení zásady CAS zakázaná v rozhraní .NET Framework 4 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="b19d0-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="b19d0-146">Pokud nastavíte `enabled` k `true`, vzdálené sestavení jsou udělena úplná důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="b19d0-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="b19d0-147">Pokud `enabled` není nastavená na `true`, <xref:System.IO.FileLoadException> je vyvolána v rámci některý z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="b19d0-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="b19d0-148">Chování sandboxing aktuální domény se liší od chování v rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="b19d0-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="b19d0-149">To vyžaduje zásady CAS se deaktivuje a aktuální doména by se v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="b19d0-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="b19d0-150">Načítané sestavení se nenachází `MyComputer` zóny.</span><span class="sxs-lookup"><span data-stu-id="b19d0-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="b19d0-151">Nastavení `<loadFromRemoteSources>` elementu `true` brání vyvolání této výjimky.</span><span class="sxs-lookup"><span data-stu-id="b19d0-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="b19d0-152">Umožňuje určit, že se spoléhá na modul common language runtime do izolovaného prostoru načtená sestavení pro zabezpečení a, může být povoleno spustit v plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="b19d0-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="b19d0-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b19d0-153">Notes</span></span>

- <span data-ttu-id="b19d0-154">V rozhraní .NET Framework 4.5 a novější verze sestavení na místní síťové sdílené složky v úplném vztahu důvěryhodnosti ve výchozím nastavení spouští; Nemáte povolení `<loadFromRemoteSources>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b19d0-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="b19d0-155">Pokud aplikace byl zkopírován z webu, je označena příznakem Windows jako webovou aplikaci, i v případě, že se nachází v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="b19d0-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="b19d0-156">Tento výběr můžete změnit změnou vlastnosti souboru, nebo můžete použít `<loadFromRemoteSources>` element udělte sestavení úplné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="b19d0-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="b19d0-157">Jako alternativu můžete použít <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metoda načíst místní sestavení, který operační systém označil jako byla načtena z webu.</span><span class="sxs-lookup"><span data-stu-id="b19d0-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="b19d0-158">Může se zobrazit <xref:System.IO.FileLoadException> v aplikaci, na kterém běží v aplikaci Windows Virtual PC.</span><span class="sxs-lookup"><span data-stu-id="b19d0-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="b19d0-159">K tomu může dojít při pokusu o načtení souboru z propojené složky na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="b19d0-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="b19d0-160">Může dojít také při pokusu o načtení souboru ze složky propojené přes [služby Vzdálená plocha](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminálové služby).</span><span class="sxs-lookup"><span data-stu-id="b19d0-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="b19d0-161">Abyste zabránili výjimku, nastavte `enabled` k `true`.</span><span class="sxs-lookup"><span data-stu-id="b19d0-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="b19d0-162">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="b19d0-162">Configuration file</span></span>

<span data-ttu-id="b19d0-163">Tento prvek je obvykle používaných v konfiguračním souboru aplikace, ale je možné v další konfigurační soubory v závislosti na kontextu.</span><span class="sxs-lookup"><span data-stu-id="b19d0-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="b19d0-164">Další informace najdete v článku [další implicitní používá certifikační Autority zásad: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) v blogu .NET Security.</span><span class="sxs-lookup"><span data-stu-id="b19d0-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="b19d0-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="b19d0-165">Example</span></span>

<span data-ttu-id="b19d0-166">Následující příklad ukazuje, jak udělit úplný vztah důvěryhodnosti k sestavení načtená ze vzdáleného zdroje.</span><span class="sxs-lookup"><span data-stu-id="b19d0-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="b19d0-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b19d0-167">See also</span></span>

- [<span data-ttu-id="b19d0-168">Více implicitní používá zásady CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="b19d0-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="b19d0-169">Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="b19d0-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="b19d0-170">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="b19d0-170">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b19d0-171">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b19d0-171">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
