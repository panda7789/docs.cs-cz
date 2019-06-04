---
title: Element <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab9feaa1c46a45471395fd4c6158490a24882a65
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489362"
---
# <a name="supportportability-element"></a><span data-ttu-id="b3dc4-102">\<supportPortability > – Element</span><span class="sxs-lookup"><span data-stu-id="b3dc4-102">\<supportPortability> Element</span></span>
<span data-ttu-id="b3dc4-103">Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích rozhraní .NET Framework zakázáním výchozího chování, které považuje za ekvivalent pro účely přenositelnosti aplikace sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="b3dc4-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="b3dc4-104">\<configuration> Element</span></span>  
<span data-ttu-id="b3dc4-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="b3dc4-105">\<runtime> Element</span></span>  
<span data-ttu-id="b3dc4-106">\<assemblybinding – > – Element</span><span class="sxs-lookup"><span data-stu-id="b3dc4-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="b3dc4-107">\<supportPortability > – Element</span><span class="sxs-lookup"><span data-stu-id="b3dc4-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3dc4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3dc4-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3dc4-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b3dc4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b3dc4-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3dc4-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b3dc4-111">Attributes</span></span>  
  
|<span data-ttu-id="b3dc4-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b3dc4-112">Attribute</span></span>|<span data-ttu-id="b3dc4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b3dc4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3dc4-114">PKT</span><span class="sxs-lookup"><span data-stu-id="b3dc4-114">PKT</span></span>|<span data-ttu-id="b3dc4-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="b3dc4-116">Určuje token veřejného klíče dotčeného sestavení jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="b3dc4-117">enabled</span><span class="sxs-lookup"><span data-stu-id="b3dc4-117">enabled</span></span>|<span data-ttu-id="b3dc4-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b3dc4-119">Určuje, zda by měla být povolena podpora pro přenositelnost mezi implementacemi zadaného sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b3dc4-120">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="b3dc4-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="b3dc4-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b3dc4-121">Value</span></span>|<span data-ttu-id="b3dc4-122">Popis</span><span class="sxs-lookup"><span data-stu-id="b3dc4-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b3dc4-123">true</span><span class="sxs-lookup"><span data-stu-id="b3dc4-123">true</span></span>|<span data-ttu-id="b3dc4-124">Povolte podporu pro přenositelnost mezi implementacemi zadaného sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="b3dc4-125">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-125">This is the default.</span></span>|  
|<span data-ttu-id="b3dc4-126">false</span><span class="sxs-lookup"><span data-stu-id="b3dc4-126">false</span></span>|<span data-ttu-id="b3dc4-127">Zakažte podporu pro přenositelnost mezi implementacemi zadaného sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="b3dc4-128">To umožňuje aplikaci mít odkazy na více implementací zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3dc4-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b3dc4-129">Child Elements</span></span>  
 <span data-ttu-id="b3dc4-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3dc4-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3dc4-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b3dc4-131">Parent Elements</span></span>  
  
|<span data-ttu-id="b3dc4-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="b3dc4-132">Element</span></span>|<span data-ttu-id="b3dc4-133">Popis</span><span class="sxs-lookup"><span data-stu-id="b3dc4-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b3dc4-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b3dc4-135">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="b3dc4-136">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3dc4-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3dc4-137">Remarks</span></span>  
 <span data-ttu-id="b3dc4-138">Od verze rozhraní .NET Framework 4, podpora je poskytována automaticky pro aplikace, které můžete použít jednu ze dvou implementací rozhraní .NET Framework, například pro implementaci rozhraní .NET Framework nebo .NET Framework pro implementaci Silverlight.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-138">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="b3dc4-139">Tyto dvě implementace konkrétního sestavení rozhraní .NET Framework jsou vázacím objektem sestavení považovány za ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="b3dc4-140">V několika scénářích tato funkce přenositelnosti aplikace způsobuje problémy.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="b3dc4-141">V těchto případech `<supportPortability>` elementu je možné zakázat funkci.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="b3dc4-142">Jeden takový scénář je sestavení, které musí odkazovat implementaci rozhraní .NET Framework a .NET Framework pro implementaci Silverlight sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="b3dc4-143">Například Návrhář XAML, zapsán ve Windows Presentation Foundation (WPF) může být nutné odkazovat oba WPF plochy implementace, návrháře uživatelské rozhraní a na podmnožinu WPF, která je součástí implementace Silverlight.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="b3dc4-144">Ve výchozím nastavení samostatné odkazy zapříčiní chybu kompilátoru, protože vazba sestavení chápe daná dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="b3dc4-145">Tento prvek zakazuje výchozí chování a umožňuje, aby kompilace proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3dc4-146">Aby kompilátor mohl předat informace pro vytváření vazeb sestavení logiky common language runtime, je nutné použít `/appconfig` – možnost kompilátoru k určení umístění souboru app.config, který obsahuje tento element.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3dc4-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3dc4-147">Example</span></span>  
 <span data-ttu-id="b3dc4-148">Následující příklad umožňuje aplikaci mít odkazy na implementaci rozhraní .NET Framework a .NET Framework pro implementaci Silverlight žádné sestavení rozhraní .NET Framework, která existuje v obou implementacích.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="b3dc4-149">`/appconfig` Kompilátoru možnost musí být použita ke specifikaci umístění tohoto app.config souboru.</span><span class="sxs-lookup"><span data-stu-id="b3dc4-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3dc4-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3dc4-150">See also</span></span>

- [<span data-ttu-id="b3dc4-151">/ appconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b3dc4-151">/appconfig (C# Compiler Options)</span></span>](../../../../../docs/csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="b3dc4-152">[Přehled sjednocení sestavení rozhraní .NET framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b3dc4-152">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
