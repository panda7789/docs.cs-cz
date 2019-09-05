---
title: Element <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 011793006f2aff32486fbe4537b46517e0a2b888
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252308"
---
# <a name="supportportability-element"></a><span data-ttu-id="6d306-102">\<Značka supportPortability – element ></span><span class="sxs-lookup"><span data-stu-id="6d306-102">\<supportPortability> Element</span></span>
<span data-ttu-id="6d306-103">Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích .NET Framework tím, že zakáže výchozí chování, které zpracovává sestavení jako ekvivalent pro účely přenositelnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d306-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
<span data-ttu-id="6d306-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6d306-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6d306-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="6d306-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6d306-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="6d306-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="6d306-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Značka supportPortability >**</span><span class="sxs-lookup"><span data-stu-id="6d306-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d306-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d306-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d306-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d306-109">Attributes and Elements</span></span>  

<span data-ttu-id="6d306-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d306-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d306-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d306-111">Attributes</span></span>  
  
|<span data-ttu-id="6d306-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6d306-112">Attribute</span></span>|<span data-ttu-id="6d306-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6d306-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d306-114">PKT</span><span class="sxs-lookup"><span data-stu-id="6d306-114">PKT</span></span>|<span data-ttu-id="6d306-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d306-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="6d306-116">Určuje token veřejného klíče pro ovlivněné sestavení jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="6d306-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="6d306-117">enabled</span><span class="sxs-lookup"><span data-stu-id="6d306-117">enabled</span></span>|<span data-ttu-id="6d306-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d306-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d306-119">Určuje, zda by měla být povolena podpora přenositelnosti mezi implementacemi zadaného .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d306-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6d306-120">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="6d306-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="6d306-121">Value</span><span class="sxs-lookup"><span data-stu-id="6d306-121">Value</span></span>|<span data-ttu-id="6d306-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6d306-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d306-123">true</span><span class="sxs-lookup"><span data-stu-id="6d306-123">true</span></span>|<span data-ttu-id="6d306-124">Povolí podporu přenositelnosti mezi implementacemi zadaného .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d306-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="6d306-125">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="6d306-125">This is the default.</span></span>|  
|<span data-ttu-id="6d306-126">false</span><span class="sxs-lookup"><span data-stu-id="6d306-126">false</span></span>|<span data-ttu-id="6d306-127">Zakažte podporu přenositelnosti mezi implementacemi zadaného .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d306-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="6d306-128">To umožňuje, aby aplikace měla odkazy na více implementací určeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d306-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d306-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d306-129">Child Elements</span></span>  

<span data-ttu-id="6d306-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="6d306-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d306-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d306-131">Parent Elements</span></span>  
  
|<span data-ttu-id="6d306-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d306-132">Element</span></span>|<span data-ttu-id="6d306-133">Popis</span><span class="sxs-lookup"><span data-stu-id="6d306-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6d306-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d306-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6d306-135">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="6d306-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="6d306-136">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d306-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d306-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d306-137">Remarks</span></span>  

<span data-ttu-id="6d306-138">Počínaje .NET Framework 4 je podpora automaticky poskytována pro aplikace, které mohou používat jednu ze dvou implementací .NET Framework, například implementaci .NET Framework nebo .NET Framework pro implementaci Silverlight.</span><span class="sxs-lookup"><span data-stu-id="6d306-138">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="6d306-139">Dvě implementace konkrétního sestavení .NET Framework jsou v pořadači sestavení zobrazeny jako ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="6d306-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="6d306-140">V několika scénářích Tato funkce přenositelnosti aplikace způsobuje problémy.</span><span class="sxs-lookup"><span data-stu-id="6d306-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="6d306-141">V těchto scénářích `<supportPortability>` lze prvek použít k zakázání funkce.</span><span class="sxs-lookup"><span data-stu-id="6d306-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="6d306-142">Jedním z takových scénářů je sestavení, které má odkazovat jak na implementaci .NET Framework, tak na .NET Framework pro implementaci Silverlightu konkrétního referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d306-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="6d306-143">Například Návrhář XAML napsaný v Windows Presentation Foundation (WPF) může potřebovat odkaz na implementaci WPF Desktop, pro uživatelské rozhraní návrháře a podmnožinu WPF, která je součástí implementace Silverlight.</span><span class="sxs-lookup"><span data-stu-id="6d306-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="6d306-144">Ve výchozím nastavení samostatné odkazy způsobí chybu kompilátoru, protože vazba sestavení uvidí dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="6d306-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="6d306-145">Tento prvek zakáže výchozí chování a umožňuje, aby kompilace proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="6d306-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6d306-146">Aby mohl kompilátor předat informace do logiky vytváření vazeb sestavení (Common Language Runtime), je nutné použít `/appconfig` možnost kompilátoru k určení umístění souboru App. config, který obsahuje tento prvek.</span><span class="sxs-lookup"><span data-stu-id="6d306-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d306-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d306-147">Example</span></span>  

<span data-ttu-id="6d306-148">Následující příklad umožňuje, aby aplikace měla odkazy na implementaci .NET Framework a .NET Framework pro implementaci technologie Silverlight pro jakékoli .NET Framework sestavení, které existuje v obou implementacích.</span><span class="sxs-lookup"><span data-stu-id="6d306-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="6d306-149">Možnost `/appconfig` kompilátoru se musí použít k určení umístění tohoto souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="6d306-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d306-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d306-150">See also</span></span>

- [<span data-ttu-id="6d306-151">/appconfig (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="6d306-151">/appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="6d306-152">[Přehled sjednocení .NET Framework sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6d306-152">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
