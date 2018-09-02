---
title: -appconfig (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 33f79967c34736f2175e0bb6e2b5b88d211545c2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398505"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="28eac-102">-appconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="28eac-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="28eac-103">**- Appconfig** – možnost kompilátoru umožňuje aplikaci v C# k určení umístění sestavení aplikace konfiguračního souboru (app.config) do common language runtime (CLR) v době vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="28eac-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28eac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28eac-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="28eac-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="28eac-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="28eac-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="28eac-106">Required.</span></span> <span data-ttu-id="28eac-107">Konfigurační soubor aplikace obsahující nastavení vazeb sestavení.</span><span class="sxs-lookup"><span data-stu-id="28eac-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28eac-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28eac-108">Remarks</span></span>  
 <span data-ttu-id="28eac-109">Jedno použití **- appconfig** je pokročilé scénáře, ve kterých má sestavení tak, aby odkazovaly na verzi rozhraní .NET Framework a .NET Framework programu Silverlight daného sestavení ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="28eac-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="28eac-110">Například Návrhář XAML, zapsán ve Windows Presentation Foundation (WPF) pravděpodobně tak, aby odkazovaly na WPF plochu, pro návrháře uživatelské rozhraní a na podmnožinu WPF, která je součástí Silverlightu.</span><span class="sxs-lookup"><span data-stu-id="28eac-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="28eac-111">Stejného návrháře sestavení má přístup k obě sestavení.</span><span class="sxs-lookup"><span data-stu-id="28eac-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="28eac-112">Ve výchozím nastavení samostatné odkazy zapříčiní chybu kompilátoru, protože vazba sestavení chápe daná dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="28eac-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="28eac-113">**- Appconfig** – možnost kompilátoru umožňuje určit umístění souboru app.config, který zakazuje výchozí chování pomocí `<supportPortability>` označit, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="28eac-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="28eac-114">Kompilátor předá umístění souboru modulu CLR vytváření vazeb sestavení logiky.</span><span class="sxs-lookup"><span data-stu-id="28eac-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28eac-115">Pokud používáte Microsoft Build Engine (MSBuild) k sestavení aplikace, můžete nastavit **- appconfig** – možnost kompilátoru přidáním tag vlastnosti do souboru csproj.</span><span class="sxs-lookup"><span data-stu-id="28eac-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="28eac-116">Použití souboru app.config, který je již nastaven v projektu, přidejte vlastnost značku `<UseAppConfigForCompiler>` do souboru .csproj souboru a nastavte jej na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="28eac-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="28eac-117">K určení různých app.config soubor, přidejte vlastnost značku `<AppConfigForCompiler>` a nastavení jeho hodnoty k umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="28eac-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28eac-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="28eac-118">Example</span></span>  
 <span data-ttu-id="28eac-119">Následující příklad ukazuje soubor app.config, který umožňuje aplikaci mít odkazy na implementaci rozhraní .NET Framework a .NET Framework pro implementaci Silverlight žádné sestavení rozhraní .NET Framework, která existuje v obou implementacích.</span><span class="sxs-lookup"><span data-stu-id="28eac-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="28eac-120">**- Appconfig** – možnost kompilátoru Určuje umístění tohoto app.config souboru.</span><span class="sxs-lookup"><span data-stu-id="28eac-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28eac-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="28eac-121">See Also</span></span>  

- [<span data-ttu-id="28eac-122">\<supportPortability > – Element</span><span class="sxs-lookup"><span data-stu-id="28eac-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
- [<span data-ttu-id="28eac-123">Možnosti kompilátoru jazyka C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="28eac-123">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
