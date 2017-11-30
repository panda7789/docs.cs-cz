---
title: "-appconfig (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /appconfig
helpviewer_keywords: /appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca752c6264d0ee886aa4c248738097e0caf1d756
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="appconfig-c-compiler-options"></a><span data-ttu-id="dcded-102">/appconfig (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="dcded-102">/appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="dcded-103">**/Appconfig** – možnost kompilátoru umožňuje aplikaci C# k určení umístění souboru konfigurace (app.config) sestavení aplikace do common language runtime (CLR) v době vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="dcded-103">The **/appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcded-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcded-104">Syntax</span></span>  
  
```console  
/appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="dcded-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dcded-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="dcded-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="dcded-106">Required.</span></span> <span data-ttu-id="dcded-107">Konfigurační soubor aplikace, který obsahuje nastavení vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="dcded-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcded-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcded-108">Remarks</span></span>  
 <span data-ttu-id="dcded-109">Jedno použití **/appconfig** je pokročilé scénáře, ve kterých má sestavení tak, aby odkazovaly na verzi rozhraní .NET Framework a rozhraní .NET Framework pro Silverlight verzi sestavení ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="dcded-109">One use of **/appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="dcded-110">Například může mít návrháře XAML napsané v systému Windows Presentation Foundation (WPF) tak, aby odkazovaly na WPF plochu, pro uživatelské rozhraní nástroje designer a do něj podmnožinu WPF, která je součástí Silverlight.</span><span class="sxs-lookup"><span data-stu-id="dcded-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="dcded-111">Do stejného sestavení návrháře má přístup k obě sestavení.</span><span class="sxs-lookup"><span data-stu-id="dcded-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="dcded-112">Ve výchozím nastavení odkazy na samostatné způsobit chybu kompilátoru, protože sestavení – vazby vidí dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="dcded-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="dcded-113">**/Appconfig** – možnost kompilátoru umožňuje určit umístění souboru app.config, která zakáže výchozí chování pomocí `<supportPortability>` značka, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="dcded-113">The **/appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="dcded-114">Kompilátor předává umístění souboru logiku vazby sestavení modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="dcded-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcded-115">Pokud používáte Microsoft Build Engine (MSBuild) Chcete-li sestavit aplikaci, můžete nastavit **/appconfig** – možnost kompilátoru přidáním vlastnost značku do souboru .csproj.</span><span class="sxs-lookup"><span data-stu-id="dcded-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **/appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="dcded-116">Pokud chcete použít soubor app.config, který je již nastaven v projektu, přidání značka vlastnost `<UseAppConfigForCompiler>` k .csproj souboru a jeho hodnotu nastavte `true`.</span><span class="sxs-lookup"><span data-stu-id="dcded-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="dcded-117">Zadat soubor app.config jiný, přidejte značku vlastnost `<AppConfigForCompiler>` a jeho hodnotu nastavte na umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="dcded-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcded-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="dcded-118">Example</span></span>  
 <span data-ttu-id="dcded-119">Následující příklad ukazuje soubor app.config, která umožňuje aplikaci tak, aby měl odkazy na implementace rozhraní .NET Framework a rozhraní .NET Framework pro Silverlight implementaci žádné sestavení rozhraní .NET Framework, který již existuje v obou implementace.</span><span class="sxs-lookup"><span data-stu-id="dcded-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="dcded-120">**/Appconfig** – možnost kompilátoru Určuje umístění pro tento soubor app.config.</span><span class="sxs-lookup"><span data-stu-id="dcded-120">The **/appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcded-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcded-121">See Also</span></span>  
 [<span data-ttu-id="dcded-122">\<supportPortability – > elementu</span><span class="sxs-lookup"><span data-stu-id="dcded-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [<span data-ttu-id="dcded-123">Možnosti kompilátoru C# uvedené podle abecedy</span><span class="sxs-lookup"><span data-stu-id="dcded-123">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
