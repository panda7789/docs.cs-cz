---
title: '&lt;loadfromremotesources –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d442f71a0e2fc7deacd9aaa02cfba7b66f2349
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a><span data-ttu-id="47ee3-102">&lt;loadfromremotesources –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="47ee3-102">&lt;loadFromRemoteSources&gt; Element</span></span>
<span data-ttu-id="47ee3-103">Určuje, zda sestavení ze vzdáleného zdroje udělení úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="47ee3-103">Specifies whether assemblies from remote sources should be granted full trust.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47ee3-104">Jestliže byly pokyn k tomuto tématu, z důvodu chybovou zprávu v seznamu chyb projektu sady Visual Studio nebo chybě sestavení, najdete v části [postupy: použití sestavení z webu v sadě Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span><span class="sxs-lookup"><span data-stu-id="47ee3-104">If you were directed to this topic because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span></span>  
  
 <span data-ttu-id="47ee3-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="47ee3-105">\<configuration></span></span>  
<span data-ttu-id="47ee3-106">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="47ee3-106">\<runtime></span></span>  
<span data-ttu-id="47ee3-107">\<loadfromremotesources – ></span><span class="sxs-lookup"><span data-stu-id="47ee3-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47ee3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47ee3-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47ee3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="47ee3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="47ee3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="47ee3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47ee3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="47ee3-111">Attributes</span></span>  
  
|<span data-ttu-id="47ee3-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="47ee3-112">Attribute</span></span>|<span data-ttu-id="47ee3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="47ee3-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="47ee3-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="47ee3-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="47ee3-115">Určuje, zda sestavení, které je načtena ze vzdáleného zdroje udělení úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="47ee3-115">Specifies whether an assembly that is loaded from remote sources should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="47ee3-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="47ee3-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="47ee3-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="47ee3-117">Value</span></span>|<span data-ttu-id="47ee3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="47ee3-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="47ee3-119">Neudělujte úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="47ee3-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="47ee3-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="47ee3-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="47ee3-121">Udělit úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="47ee3-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47ee3-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="47ee3-122">Child Elements</span></span>  
 <span data-ttu-id="47ee3-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="47ee3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47ee3-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="47ee3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="47ee3-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="47ee3-125">Element</span></span>|<span data-ttu-id="47ee3-126">Popis</span><span class="sxs-lookup"><span data-stu-id="47ee3-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="47ee3-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47ee3-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="47ee3-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="47ee3-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47ee3-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47ee3-129">Remarks</span></span>  
 <span data-ttu-id="47ee3-130">V rozhraní .NET Framework verze 3.5 a starší verze když se načíst sestavení ze vzdáleného umístění, sestavení spuštěná částečně důvěryhodné se sadou udělení, která závisí na zónu, ve které byla načtena.</span><span class="sxs-lookup"><span data-stu-id="47ee3-130">In the .NET Framework version 3.5 and earlier versions, if you loaded an assembly from a remote location, the assembly would run partially trusted with a grant set that depended on the zone in which it was loaded.</span></span> <span data-ttu-id="47ee3-131">Například pokud načtení sestavení z webu ho byla načtena do zóně Internet a udělit oprávnění sadu Internet.</span><span class="sxs-lookup"><span data-stu-id="47ee3-131">For example, if you loaded an assembly from a website, it was loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="47ee3-132">Jinými slovy spustit v izolovaného prostoru Internetu.</span><span class="sxs-lookup"><span data-stu-id="47ee3-132">In other words, it executed in an Internet sandbox.</span></span> <span data-ttu-id="47ee3-133">Pokud spustíte této sestavě [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a novější verze, je vyvolána výjimka, musí explicitně vytvořit izolovaný prostor pro sestavení (najdete v části [postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), nebo spustit v režimu plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="47ee3-133">If you try to run that assembly in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later versions, an exception is thrown; you must either explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), or run it in full trust.</span></span>  
  
 <span data-ttu-id="47ee3-134">`<loadFromRemoteSources>` Element umožňuje určit, že sestavení, která by mít spuštění částečně důvěryhodného v dřívějších verzích rozhraní .NET Framework musí být plně spuštěny v důvěryhodné [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="47ee3-134">The `<loadFromRemoteSources>` element lets you specify that the assemblies that would have run partially trusted in earlier versions of the .NET Framework are to be run fully trusted in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="47ee3-135">Ve výchozím nastavení, vzdálené sestavení se nespustí [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="47ee3-135">By default, remote assemblies do not run in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span> <span data-ttu-id="47ee3-136">Ke spuštění vzdálené sestavení, musíte buď spustit jako plně důvěryhodná nebo vytvořit v izolovaném prostoru <xref:System.AppDomain> ve kterém se má spustit.</span><span class="sxs-lookup"><span data-stu-id="47ee3-136">To run a remote assembly, you must either run it as fully trusted or create a sandboxed <xref:System.AppDomain> in which to run it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47ee3-137">V [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], sestavení na místní síťové sdílené složky jsou spustit jako úplný vztah důvěryhodnosti ve výchozím nastavení; není třeba povolit `<loadFromRemoteSources>` elementu.</span><span class="sxs-lookup"><span data-stu-id="47ee3-137">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies on local network shares are run as full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47ee3-138">Pokud aplikace byl zkopírován z webu, je označené v systému Windows jako webové aplikace, i v případě, že se nachází v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="47ee3-138">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="47ee3-139">Tento výběr můžete změnit změnou vlastností souboru, nebo můžete použít `<loadFromRemoteSources>` elementu, který chcete udělit sestavení úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="47ee3-139">You can change that designation by changing the file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="47ee3-140">Jako alternativu, můžete použít <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metoda načíst místní sestavení, které operační systém má označení s bylo načteno z webu.</span><span class="sxs-lookup"><span data-stu-id="47ee3-140">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>  
  
 <span data-ttu-id="47ee3-141">`enabled` Atributů pro tento element je platná pouze v případě, že zabezpečení přístupu kódu (CAS) je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="47ee3-141">The `enabled` attribute for this element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="47ee3-142">Ve výchozím nastavení, certifikační Autority zásada je zakázána v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="47ee3-142">By default, CAS policy is disabled in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="47ee3-143">Pokud nastavíte `enabled` k `true`, vzdálené aplikace mají úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="47ee3-143">If you set `enabled` to `true`, remote applications are granted full trust.</span></span>  
  
 <span data-ttu-id="47ee3-144">Pokud `<loadFromRemoteSources>``enabled` není nastavený na `true`, je vyvolána výjimka za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="47ee3-144">If `<loadFromRemoteSources>``enabled` is not set to `true`, an exception is thrown under the following conditions:</span></span>  
  
-   <span data-ttu-id="47ee3-145">Chování sandboxing aktuální doméně se liší od jeho chování [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="47ee3-145">The sandboxing behavior of the current domain is different from its behavior in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="47ee3-146">To vyžaduje zásadu CAS se zakáže a aktuální doméně není v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="47ee3-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>  
  
-   <span data-ttu-id="47ee3-147">Sestavení načítá není z `MyComputer` zóny.</span><span class="sxs-lookup"><span data-stu-id="47ee3-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47ee3-148">Může dojít <xref:System.IO.FileLoadException> v aplikaci Windows Virtual PC při pokusu načíst soubor ze propojené složek na hostitelský počítač.</span><span class="sxs-lookup"><span data-stu-id="47ee3-148">You may get a <xref:System.IO.FileLoadException> in a Windows Virtual PC application when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="47ee3-149">K této chybě může dojít při pokusu načíst soubor ze složky propojené přes [služby Vzdálená plocha](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminálové služby).</span><span class="sxs-lookup"><span data-stu-id="47ee3-149">This error may also occur when you try to load a file from a folder linked over [Remote Desktop Services](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="47ee3-150">Abyste se vyhnuli výjimku, nastavte `enabled` k `true`.</span><span class="sxs-lookup"><span data-stu-id="47ee3-150">To avoid the exception, set `enabled` to `true`.</span></span>  
  
 <span data-ttu-id="47ee3-151">Nastavení `<loadFromRemoteSources>` element `true` zabraňuje vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="47ee3-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="47ee3-152">Umožňuje zadat, že nejsou spoléhat na modul CLR do izolovaného prostoru načíst sestavení pro zabezpečení a že může být povolené provést jako úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="47ee3-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute as full trust.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="47ee3-153">Pokud sestavení by neměla běžet v režimu plné důvěryhodnosti, nenastavujte tento element konfigurace.</span><span class="sxs-lookup"><span data-stu-id="47ee3-153">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="47ee3-154">Místo toho vytvořte v izolovaném prostoru <xref:System.AppDomain> ve kterém se načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="47ee3-154">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="47ee3-155">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="47ee3-155">Configuration File</span></span>  
 <span data-ttu-id="47ee3-156">Tento prvek se obvykle používá v konfiguračním souboru aplikace, ale mohou být používány další konfigurační soubory v závislosti na kontextu.</span><span class="sxs-lookup"><span data-stu-id="47ee3-156">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="47ee3-157">Další informace najdete v článku [další implicitní používá certifikační Autority zásad: loadfromremotesources –](http://go.microsoft.com/fwlink/p/?LinkId=266839) v blogu zabezpečení rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="47ee3-157">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ee3-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="47ee3-158">Example</span></span>  
 <span data-ttu-id="47ee3-159">Následující příklad ukazuje, jak udělit úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="47ee3-159">The following example shows how to grant full trust to applications from remote sources.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47ee3-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="47ee3-160">See Also</span></span>  
 [<span data-ttu-id="47ee3-161">Více implicitní používá certifikační Autority zásad: loadfromremotesources –</span><span class="sxs-lookup"><span data-stu-id="47ee3-161">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [<span data-ttu-id="47ee3-162">Postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="47ee3-162">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="47ee3-163">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="47ee3-163">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="47ee3-164">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="47ee3-164">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
