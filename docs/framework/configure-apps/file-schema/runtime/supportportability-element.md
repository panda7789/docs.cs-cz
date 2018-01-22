---
title: "&lt;supportPortability –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52ef9cce9ee28c6329f688bb9ac751f0f9016657
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltsupportportabilitygt-element"></a><span data-ttu-id="ca2b4-102">&lt;supportPortability –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="ca2b4-102">&lt;supportPortability&gt; Element</span></span>
<span data-ttu-id="ca2b4-103">Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementace rozhraní .NET Framework zakázáním výchozí chování, která zpracovává sestavení jako ekvivalentní pro účely přenositelnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="ca2b4-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="ca2b4-104">\<configuration> Element</span></span>  
<span data-ttu-id="ca2b4-105">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="ca2b4-105">\<runtime> Element</span></span>  
<span data-ttu-id="ca2b4-106">\<assemblybinding – > elementu</span><span class="sxs-lookup"><span data-stu-id="ca2b4-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="ca2b4-107">\<supportPortability – > elementu</span><span class="sxs-lookup"><span data-stu-id="ca2b4-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca2b4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca2b4-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca2b4-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ca2b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ca2b4-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca2b4-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ca2b4-111">Attributes</span></span>  
  
|<span data-ttu-id="ca2b4-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ca2b4-112">Attribute</span></span>|<span data-ttu-id="ca2b4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ca2b4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca2b4-114">PKT</span><span class="sxs-lookup"><span data-stu-id="ca2b4-114">PKT</span></span>|<span data-ttu-id="ca2b4-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca2b4-116">Určuje token veřejného klíče ovlivněných sestavení jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="ca2b4-117">povoleno</span><span class="sxs-lookup"><span data-stu-id="ca2b4-117">enabled</span></span>|<span data-ttu-id="ca2b4-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ca2b4-119">Určuje, zda se má povolit podpora přenositelnost mezi implementace zadané sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ca2b4-120">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="ca2b4-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="ca2b4-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ca2b4-121">Value</span></span>|<span data-ttu-id="ca2b4-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ca2b4-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ca2b4-123">true</span><span class="sxs-lookup"><span data-stu-id="ca2b4-123">true</span></span>|<span data-ttu-id="ca2b4-124">Povolení podpory pro přenositelnost mezi implementace zadané sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="ca2b4-125">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-125">This is the default.</span></span>|  
|<span data-ttu-id="ca2b4-126">false</span><span class="sxs-lookup"><span data-stu-id="ca2b4-126">false</span></span>|<span data-ttu-id="ca2b4-127">Zakažte podporu pro přenositelnost mezi implementace zadané sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="ca2b4-128">To umožňuje aplikaci odkazují na více implementace zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca2b4-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ca2b4-129">Child Elements</span></span>  
 <span data-ttu-id="ca2b4-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="ca2b4-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca2b4-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ca2b4-131">Parent Elements</span></span>  
  
|<span data-ttu-id="ca2b4-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="ca2b4-132">Element</span></span>|<span data-ttu-id="ca2b4-133">Popis</span><span class="sxs-lookup"><span data-stu-id="ca2b4-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ca2b4-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ca2b4-135">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="ca2b4-136">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca2b4-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca2b4-137">Remarks</span></span>  
 <span data-ttu-id="ca2b4-138">Od verze [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], podpora je k dispozici automaticky pro aplikace, které můžete použít buď dva implementace rozhraní .NET Framework, například buď implementace rozhraní .NET Framework nebo .NET Framework pro Silverlight implementaci.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="ca2b4-139">Dva implementace konkrétní sestavení rozhraní .NET Framework se zobrazují jako ekvivalentní podle vazač sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="ca2b4-140">Tato funkce přenositelnost aplikace v několik scénářů, způsobuje problémy.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="ca2b4-141">V těchto případech `<supportPortability>` prvek můžete použít funkci zakážete.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="ca2b4-142">Jeden z těchto důvodů je sestavení, který má odkazovat implementace rozhraní .NET Framework a rozhraní .NET Framework pro Silverlight implementaci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="ca2b4-143">Návrhář XAML napsané v systému Windows Presentation Foundation (WPF) možná muset odkazovat oba WPF plochy implementaci, pro uživatelské rozhraní nástroje designer a do něj podmnožinu WPF, který je součástí implementace Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="ca2b4-144">Ve výchozím nastavení odkazy na samostatné způsobit chybu kompilátoru, protože sestavení – vazby vidí dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="ca2b4-145">Tento element zakáže výchozí chování a umožňuje kompilace proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ca2b4-146">Aby kompilátoru k předání informací pro modul common language runtime vazby sestavení logiky, je nutné použít `/appconfig` – možnost kompilátoru k určení umístění souboru app.config, který obsahuje tento element.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca2b4-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca2b4-147">Example</span></span>  
 <span data-ttu-id="ca2b4-148">Následující příklad povolí aplikaci tak, aby měl odkazy na implementace rozhraní .NET Framework a rozhraní .NET Framework pro Silverlight implementaci žádné sestavení rozhraní .NET Framework, který již existuje v obou implementace.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="ca2b4-149">`/appconfig` – Možnost kompilátoru použije k určení umístění tohoto souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca2b4-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca2b4-150">See Also</span></span>  
 [<span data-ttu-id="ca2b4-151">/ appconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ca2b4-151">/appconfig (C# Compiler Options)</span></span>](http://msdn.microsoft.com/library/ee523958.aspx)  
 [<span data-ttu-id="ca2b4-152">Přehled sjednocení sestavení rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="ca2b4-152">.NET Framework Assembly Unification Overview</span></span>](http://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
