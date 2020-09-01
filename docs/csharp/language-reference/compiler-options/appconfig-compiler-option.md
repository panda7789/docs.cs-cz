---
description: -appconfig (možnosti kompilátoru C#)
title: -appconfig (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 287d41105199057add1dad78d480b083adb745b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126109"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="7a42a-103">-appconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="7a42a-103">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="7a42a-104">Možnost kompilátoru **-appconfig** umožňuje aplikaci v jazyce C# určit umístění souboru konfigurace aplikace (app.config) sestavení pro modul CLR (Common Language Runtime) v době vytváření vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a42a-104">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a42a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a42a-105">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="7a42a-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7a42a-106">Arguments</span></span>  
 `file`  
 <span data-ttu-id="7a42a-107">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7a42a-107">Required.</span></span> <span data-ttu-id="7a42a-108">Konfigurační soubor aplikace, který obsahuje nastavení vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a42a-108">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a42a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a42a-109">Remarks</span></span>  
 <span data-ttu-id="7a42a-110">Jedno použití **-appconfig** je pokročilé scénáře, ve kterých sestavení musí odkazovat jak na verzi .NET Framework, tak na .NET Framework pro verzi Silverlight konkrétního referenčního sestavení ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="7a42a-110">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="7a42a-111">Například Návrhář XAML napsaný v Windows Presentation Foundation (WPF) může být nutné odkazovat jak na Desktop WPF, tak na uživatelském rozhraní návrháře a na podmnožinu WPF, která je součástí programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="7a42a-111">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="7a42a-112">Stejné sestavení návrháře má přístup k oběma sestavením.</span><span class="sxs-lookup"><span data-stu-id="7a42a-112">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="7a42a-113">Ve výchozím nastavení samostatné odkazy způsobí chybu kompilátoru, protože vazba sestavení uvidí dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="7a42a-113">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="7a42a-114">Možnost kompilátoru **-appconfig** umožňuje určit umístění souboru app.config, který zakáže výchozí chování pomocí `<supportPortability>` značky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7a42a-114">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="7a42a-115">Kompilátor předá umístění souboru do logiky vytváření vazeb sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="7a42a-115">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a42a-116">Pokud k sestavení aplikace používáte Microsoft Build Engine (MSBuild), můžete nastavit možnost kompilátoru **-appconfig** přidáním značky vlastnosti do souboru. csproj.</span><span class="sxs-lookup"><span data-stu-id="7a42a-116">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="7a42a-117">Chcete-li použít soubor app.config, který je již nastaven v projektu, přidejte `<UseAppConfigForCompiler>` do souboru. csproj značku vlastnosti a nastavte jeho hodnotu na `true` .</span><span class="sxs-lookup"><span data-stu-id="7a42a-117">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="7a42a-118">Chcete-li zadat jiný soubor app.config, přidejte značku vlastnosti `<AppConfigForCompiler>` a nastavte její hodnotu na umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="7a42a-118">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a42a-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a42a-119">Example</span></span>  
 <span data-ttu-id="7a42a-120">Následující příklad ukazuje soubor app.config, který umožňuje aplikaci mít odkazy na implementaci .NET Framework a .NET Framework pro implementaci technologie Silverlight pro jakékoli .NET Framework sestavení, které existuje v obou implementacích.</span><span class="sxs-lookup"><span data-stu-id="7a42a-120">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="7a42a-121">Možnost kompilátoru **-appconfig** určuje umístění tohoto souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="7a42a-121">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a42a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a42a-122">See also</span></span>

- [<span data-ttu-id="7a42a-123">\<supportPortability> Objekt</span><span class="sxs-lookup"><span data-stu-id="7a42a-123">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="7a42a-124">Možnosti kompilátoru C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="7a42a-124">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
