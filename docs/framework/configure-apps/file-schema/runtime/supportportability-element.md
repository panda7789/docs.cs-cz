---
title: Element <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 63c309a8a93c1d31ed8f73a495cf5154c3590d56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115658"
---
# <a name="supportportability-element"></a><span data-ttu-id="44efa-102">Element \<supportPortability></span><span class="sxs-lookup"><span data-stu-id="44efa-102">\<supportPortability> Element</span></span>
<span data-ttu-id="44efa-103">Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích .NET Framework tím, že zakáže výchozí chování, které zpracovává sestavení jako ekvivalent pro účely přenositelnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="44efa-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a><span data-ttu-id="44efa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44efa-104">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44efa-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44efa-105">Attributes and Elements</span></span>  

<span data-ttu-id="44efa-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44efa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44efa-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="44efa-107">Attributes</span></span>  
  
|<span data-ttu-id="44efa-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="44efa-108">Attribute</span></span>|<span data-ttu-id="44efa-109">Popis</span><span class="sxs-lookup"><span data-stu-id="44efa-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44efa-110">PKT</span><span class="sxs-lookup"><span data-stu-id="44efa-110">PKT</span></span>|<span data-ttu-id="44efa-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="44efa-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="44efa-112">Určuje token veřejného klíče pro ovlivněné sestavení jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="44efa-112">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="44efa-113">enabled</span><span class="sxs-lookup"><span data-stu-id="44efa-113">enabled</span></span>|<span data-ttu-id="44efa-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44efa-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="44efa-115">Určuje, zda by měla být povolena podpora přenositelnosti mezi implementacemi zadaného .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="44efa-115">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="44efa-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="44efa-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="44efa-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="44efa-117">Value</span></span>|<span data-ttu-id="44efa-118">Description</span><span class="sxs-lookup"><span data-stu-id="44efa-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44efa-119">true</span><span class="sxs-lookup"><span data-stu-id="44efa-119">true</span></span>|<span data-ttu-id="44efa-120">Povolí podporu přenositelnosti mezi implementacemi zadaného .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="44efa-120">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="44efa-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="44efa-121">This is the default.</span></span>|  
|<span data-ttu-id="44efa-122">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="44efa-122">false</span></span>|<span data-ttu-id="44efa-123">Zakažte podporu přenositelnosti mezi implementacemi zadaného .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="44efa-123">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="44efa-124">To umožňuje, aby aplikace měla odkazy na více implementací určeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="44efa-124">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44efa-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44efa-125">Child Elements</span></span>  

<span data-ttu-id="44efa-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="44efa-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44efa-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44efa-127">Parent Elements</span></span>  
  
|<span data-ttu-id="44efa-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="44efa-128">Element</span></span>|<span data-ttu-id="44efa-129">Description</span><span class="sxs-lookup"><span data-stu-id="44efa-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="44efa-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44efa-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="44efa-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="44efa-131">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="44efa-132">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="44efa-132">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44efa-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44efa-133">Remarks</span></span>  

<span data-ttu-id="44efa-134">Počínaje .NET Framework 4 je podpora automaticky poskytována pro aplikace, které mohou používat jednu ze dvou implementací .NET Framework, například implementaci .NET Framework nebo .NET Framework pro implementaci Silverlight.</span><span class="sxs-lookup"><span data-stu-id="44efa-134">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="44efa-135">Dvě implementace konkrétního sestavení .NET Framework jsou v pořadači sestavení zobrazeny jako ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="44efa-135">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="44efa-136">V několika scénářích Tato funkce přenositelnosti aplikace způsobuje problémy.</span><span class="sxs-lookup"><span data-stu-id="44efa-136">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="44efa-137">V těchto scénářích `<supportPortability>` lze prvek použít k zakázání funkce.</span><span class="sxs-lookup"><span data-stu-id="44efa-137">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="44efa-138">Jedním z takových scénářů je sestavení, které má odkazovat jak na implementaci .NET Framework, tak na .NET Framework pro implementaci Silverlightu konkrétního referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="44efa-138">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="44efa-139">Například Návrhář XAML napsaný v Windows Presentation Foundation (WPF) může potřebovat odkaz na implementaci WPF Desktop, pro uživatelské rozhraní návrháře a podmnožinu WPF, která je součástí implementace Silverlight.</span><span class="sxs-lookup"><span data-stu-id="44efa-139">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="44efa-140">Ve výchozím nastavení samostatné odkazy způsobí chybu kompilátoru, protože vazba sestavení uvidí dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="44efa-140">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="44efa-141">Tento prvek zakáže výchozí chování a umožňuje, aby kompilace proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="44efa-141">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="44efa-142">Aby mohl kompilátor předat informace do logiky vytváření vazeb sestavení (Common Language Runtime), je nutné použít `/appconfig` možnost kompilátoru k určení umístění souboru App. config, který obsahuje tento prvek.</span><span class="sxs-lookup"><span data-stu-id="44efa-142">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44efa-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="44efa-143">Example</span></span>  

<span data-ttu-id="44efa-144">Následující příklad umožňuje, aby aplikace měla odkazy na implementaci .NET Framework a .NET Framework pro implementaci technologie Silverlight pro jakékoli .NET Framework sestavení, které existuje v obou implementacích.</span><span class="sxs-lookup"><span data-stu-id="44efa-144">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="44efa-145">`/appconfig`Možnost kompilátoru se musí použít k určení umístění tohoto souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="44efa-145">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44efa-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="44efa-146">See also</span></span>

- [<span data-ttu-id="44efa-147">-appconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="44efa-147">-appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="44efa-148">[Přehled sjednocení .NET Framework sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="44efa-148">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
