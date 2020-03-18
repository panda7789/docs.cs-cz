---
title: -appconfig (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922524"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="bdc4e-102">-appconfig (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bdc4e-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="bdc4e-103">Možnost kompilátoru **-appconfig** umožňuje aplikaci C# určit umístění souboru konfigurace aplikace sestavení (app.config) do souboru CLR (COMMON Language runtime) v době vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdc4e-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="bdc4e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bdc4e-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="bdc4e-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-106">Required.</span></span> <span data-ttu-id="bdc4e-107">Konfigurační soubor aplikace, který obsahuje nastavení vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdc4e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdc4e-108">Remarks</span></span>  
 <span data-ttu-id="bdc4e-109">Jedním z použití **-appconfig** je pokročilé scénáře, ve kterých sestavení musí odkazovat na verzi rozhraní .NET Framework a rozhraní .NET Framework pro verzi programu Silverlight konkrétního referenčního sestavení současně.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="bdc4e-110">Například návrhář XAML napsaný v systému Windows Presentation Foundation (WPF) může mít odkazovat jak wpf desktop, pro uživatelské rozhraní návrháře a podmnožinu WPF, který je součástí Programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="bdc4e-111">Stejné sestavení návrháře má přístup k oběma sestavením.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="bdc4e-112">Ve výchozím nastavení samostatné odkazy způsobit chybu kompilátoru, protože vazba sestavení vidí dvě sestavení jako ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="bdc4e-113">Možnost kompilátoru **-appconfig** umožňuje určit umístění souboru app.config, který zakáže výchozí chování pomocí `<supportPortability>` značky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="bdc4e-114">Kompilátor předá umístění souboru clr je vázající logiku sestavení.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdc4e-115">Pokud k vytvoření aplikace používáte modul Microsoft Build Engine (MSBuild), můžete nastavit možnost kompilátoru **-appconfig** přidáním značky vlastnosti do souboru .csproj.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="bdc4e-116">Chcete-li použít soubor app.config, který je již `<UseAppConfigForCompiler>` v projektu nastaven, přidejte do `true`souboru .csproj značku vlastnosti a nastavte jeho hodnotu na .</span><span class="sxs-lookup"><span data-stu-id="bdc4e-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="bdc4e-117">Chcete-li zadat jiný soubor app.config, přidejte značku `<AppConfigForCompiler>` vlastnosti a nastavte její hodnotu na umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdc4e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdc4e-118">Example</span></span>  
 <span data-ttu-id="bdc4e-119">Následující příklad ukazuje soubor app.config, který umožňuje aplikaci mít odkazy na implementaci rozhraní .NET Framework a rozhraní .NET Framework pro implementaci rozhraní Silverlight libovolného sestavení rozhraní .NET Framework, které existuje v obou implementacích.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="bdc4e-120">Možnost kompilátoru **-appconfig** určuje umístění tohoto souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="bdc4e-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bdc4e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="bdc4e-121">See also</span></span>

- [<span data-ttu-id="bdc4e-122">\<supportPortability> Element</span><span class="sxs-lookup"><span data-stu-id="bdc4e-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="bdc4e-123">Možnosti kompilátoru C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="bdc4e-123">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
