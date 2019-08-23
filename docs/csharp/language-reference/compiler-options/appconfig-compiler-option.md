---
title: -appconfig (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922524"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="0ceb2-102">-appconfig (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="0ceb2-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="0ceb2-103">Možnost kompilátoru **-appconfig** umožňuje C# aplikaci určit umístění souboru konfigurace aplikace (App. config) sestavení pro modul CLR (Common Language Runtime) v době vytváření vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ceb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ceb2-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ceb2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0ceb2-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="0ceb2-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-106">Required.</span></span> <span data-ttu-id="0ceb2-107">Konfigurační soubor aplikace, který obsahuje nastavení vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ceb2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ceb2-108">Remarks</span></span>  
 <span data-ttu-id="0ceb2-109">Jedno použití **-appconfig** je pokročilé scénáře, ve kterých sestavení musí odkazovat jak na verzi .NET Framework, tak na .NET Framework pro verzi Silverlight konkrétního referenčního sestavení ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="0ceb2-110">Například Návrhář XAML napsaný v Windows Presentation Foundation (WPF) může být nutné odkazovat jak na Desktop WPF, tak na uživatelském rozhraní návrháře a na podmnožinu WPF, která je součástí programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="0ceb2-111">Stejné sestavení návrháře má přístup k oběma sestavením.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="0ceb2-112">Ve výchozím nastavení samostatné odkazy způsobí chybu kompilátoru, protože vazba sestavení uvidí dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="0ceb2-113">Možnost kompilátoru **-appconfig** umožňuje určit umístění souboru App. config, který zakáže výchozí chování pomocí `<supportPortability>` značky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="0ceb2-114">Kompilátor předá umístění souboru do logiky vytváření vazeb sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ceb2-115">Pokud k sestavení aplikace používáte Microsoft Build Engine (MSBuild), můžete nastavit možnost kompilátoru **-appconfig** přidáním značky vlastnosti do souboru. csproj.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="0ceb2-116">Chcete-li použít soubor App. config, který je již nastaven v projektu, přidejte do `<UseAppConfigForCompiler>` souboru. csproj značku vlastnosti a nastavte jeho hodnotu na `true`.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="0ceb2-117">Chcete-li zadat jiný soubor App. config, přidejte značku `<AppConfigForCompiler>` vlastnosti a nastavte její hodnotu na umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ceb2-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ceb2-118">Example</span></span>  
 <span data-ttu-id="0ceb2-119">Následující příklad ukazuje soubor App. config, který umožňuje, aby aplikace měla odkazy na implementaci .NET Framework a .NET Framework pro implementaci technologie Silverlight pro jakékoli .NET Framework sestavení, které existuje v obou implementacích.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="0ceb2-120">Možnost kompilátoru **-appconfig** určuje umístění tohoto souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="0ceb2-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0ceb2-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ceb2-121">See also</span></span>

- [<span data-ttu-id="0ceb2-122">\<Značka supportPortability – element ></span><span class="sxs-lookup"><span data-stu-id="0ceb2-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="0ceb2-123">Možnosti kompilátoru jazyka C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="0ceb2-123">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
