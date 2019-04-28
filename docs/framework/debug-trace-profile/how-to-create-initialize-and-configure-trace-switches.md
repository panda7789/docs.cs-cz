---
title: 'Postupy: Vytváření, inicializace a konfigurace přepínačů trasování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87170035df47e7605d25531df4b0759bf121ad80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754346"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="cf796-102">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="cf796-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="cf796-103">Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="cf796-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="cf796-104">Vytváření a inicializace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="cf796-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="cf796-105">Chcete-li použít přepínačů trasování, musíte je vytvořit a umístit je do vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="cf796-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="cf796-106">Existují dvě předdefinované třídy, ze kterých můžete vytvořit objekty přepínač: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> třídy a <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="cf796-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="cf796-107">Můžete využít <xref:System.Diagnostics.BooleanSwitch> Pokud vám záleží pouze určuje, jestli se zobrazí zpráva trasování, použijete <xref:System.Diagnostics.TraceSwitch> Pokud chcete rozlišit úrovní trasování.</span><span class="sxs-lookup"><span data-stu-id="cf796-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="cf796-108">Pokud používáte <xref:System.Diagnostics.TraceSwitch>, můžete definovat vlastní zprávy ladění a spojit je s různými úrovněmi trasování.</span><span class="sxs-lookup"><span data-stu-id="cf796-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="cf796-109">Můžete použít oba typy přepínače trasování nebo ladění.</span><span class="sxs-lookup"><span data-stu-id="cf796-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="cf796-110">Ve výchozím nastavení <xref:System.Diagnostics.BooleanSwitch> zakázána a <xref:System.Diagnostics.TraceSwitch> je nastavená na úroveň <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cf796-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cf796-111">Přepínače trasování může být vytvořeno a umístí do libovolné části kódu, která může používat.</span><span class="sxs-lookup"><span data-stu-id="cf796-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="cf796-112">I když úrovní trasování a další možnosti konfigurace můžete nastavit v kódu, doporučujeme použít konfigurační soubor pro správu stavu vašich přepínače.</span><span class="sxs-lookup"><span data-stu-id="cf796-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="cf796-113">Důvodem je, že správu konfigurace vašeho přepínače v konfigurační systém poskytuje větší flexibilitu, můžete zapnout nebo vypnout různé přepínače a měnit úrovně bez opětovné kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf796-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="cf796-114">Vytvoření a inicializace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="cf796-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="cf796-115">Definování přepínač jako buď typ <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> nebo typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> a nastavte název a popis přepínače.</span><span class="sxs-lookup"><span data-stu-id="cf796-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="cf796-116">Nakonfigurujte přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="cf796-116">Configure your trace switch.</span></span> <span data-ttu-id="cf796-117">Další informace najdete v tématu [konfigurace přepínačů trasování](#configure).</span><span class="sxs-lookup"><span data-stu-id="cf796-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="cf796-118">Následující kód vytvoří dva přepínače, jeden z každého typu:</span><span class="sxs-lookup"><span data-stu-id="cf796-118">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =   
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =   
       new System.Diagnostics.TraceSwitch("General",   
       "Entire application");  
    ```  
  
<a name="configure"></a>   
## <a name="configuring-trace-switches"></a><span data-ttu-id="cf796-119">Konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="cf796-119">Configuring trace switches</span></span>  
 <span data-ttu-id="cf796-120">Poté, co vaše aplikace byla distribuována, můžete stále povolit nebo zakázat výstup trasování pomocí konfigurace přepínačů trasování ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cf796-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="cf796-121">Konfigurace přepínače znamená, že změníte jeho hodnotu z externího zdroje, jakmile byla inicializována.</span><span class="sxs-lookup"><span data-stu-id="cf796-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="cf796-122">Můžete změnit hodnoty přepínače objektů pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="cf796-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="cf796-123">Při konfiguraci přepínače trasování můžete zapnout nebo vypnout, nebo k nastavení jeho úroveň určující velikost a typ zprávy ji předá do naslouchacích procesů.</span><span class="sxs-lookup"><span data-stu-id="cf796-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="cf796-124">Vaše přepínače jsou nakonfigurováni pomocí souboru .config.</span><span class="sxs-lookup"><span data-stu-id="cf796-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="cf796-125">Pro webovou aplikaci Toto je soubor Web.config, který je přidružený k projektu.</span><span class="sxs-lookup"><span data-stu-id="cf796-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="cf796-126">V aplikaci Windows, je tento soubor s názvem (název aplikace). exe.config. V nasazené aplikaci musí být tento soubor umístěn ve stejné složce jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="cf796-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="cf796-127">Když vaše aplikace spustí kód, který vytvoří instanci přepínače poprvé, ověří konfigurační soubor pro úroveň trasování informace o pojmenovaných přepínači.</span><span class="sxs-lookup"><span data-stu-id="cf796-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="cf796-128">Systém sledování zkontroluje konfigurační soubor jen jednou pro jakékoli konkrétní přepínač – poprvé aplikace vytváří přepínač.</span><span class="sxs-lookup"><span data-stu-id="cf796-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="cf796-129">V nasazení aplikace povolíte trasování kódu opětovná konfigurace přepínače objektů, pokud aplikace neběží.</span><span class="sxs-lookup"><span data-stu-id="cf796-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="cf796-130">Obvykle to zahrnuje zapnutí přepínače objektů a vypnout nebo změnou úrovně trasování a následného restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf796-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="cf796-131">Při vytváření instance přepínače taky ji inicializovat zadáním dva argumenty: *displayName* argument a *popis* argument.</span><span class="sxs-lookup"><span data-stu-id="cf796-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="cf796-132">*DisplayName* argument konstruktoru sady <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> vlastnost <xref:System.Diagnostics.Switch> instance třídy.</span><span class="sxs-lookup"><span data-stu-id="cf796-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="cf796-133">*DisplayName* je název, který se používá ke konfiguraci přepínače v souboru .config a *popis* argument by měl vrátit stručný popis přepínač a co ho zprávy ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="cf796-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="cf796-134">Kromě zadání názvu přepínače ke konfiguraci, musíte zadat také hodnotu pro přepínač.</span><span class="sxs-lookup"><span data-stu-id="cf796-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="cf796-135">Tato hodnota je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="cf796-135">This value is an Integer.</span></span> <span data-ttu-id="cf796-136">Pro <xref:System.Diagnostics.BooleanSwitch>, hodnota 0 odpovídá **vypnout**, a odpovídá jakékoli nenulovou hodnotu **na**.</span><span class="sxs-lookup"><span data-stu-id="cf796-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="cf796-137">Pro <xref:System.Diagnostics.TraceSwitch>0,1,2,3 a 4 odpovídají **vypnout**, **chyba**, **upozornění**, **informace**, a **Verbose**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cf796-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="cf796-138">Libovolné číslo větší než 4 je považován za **Verbose**a jakékoli číslo menší než nula je považován za **vypnout**.</span><span class="sxs-lookup"><span data-stu-id="cf796-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf796-139">V rozhraní .NET Framework verze 2.0 můžete zadat hodnotu pro přepínač text.</span><span class="sxs-lookup"><span data-stu-id="cf796-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="cf796-140">Například `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo představující hodnotu výčtu, jako text `Error` pro <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="cf796-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="cf796-141">Na řádku `<add name="myTraceSwitch" value="Error" />` je ekvivalentní `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="cf796-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="cf796-142">Aby koncoví uživatelé moct konfigurace přepínačů trasování aplikace je nutné zadat podrobnou dokumentaci na přepínače ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cf796-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="cf796-143">By měla podrobně popisují, které přepínače řídit, co a jak vypnout nebo zapnout.</span><span class="sxs-lookup"><span data-stu-id="cf796-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="cf796-144">Koncový uživatel by měly také poskytnout soubor .config, který má odpovídající nápovědu v komentářích.</span><span class="sxs-lookup"><span data-stu-id="cf796-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="cf796-145">Konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="cf796-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="cf796-146">Chcete-li použít přepínačů trasování, musíte je vytvořit a umístit je do kódu, jak je popsáno v části [vytváření a inicializace přepínačů trasování](#create).</span><span class="sxs-lookup"><span data-stu-id="cf796-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="cf796-147">Pokud váš projekt neobsahuje soubor konfigurace (app.config nebo Web.config), pak z **projektu** nabídce vyberte možnost **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="cf796-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="cf796-148">**Visual Basic:** V **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.</span><span class="sxs-lookup"><span data-stu-id="cf796-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="cf796-149">Konfigurační soubor aplikace je vytvořen a otevřít.</span><span class="sxs-lookup"><span data-stu-id="cf796-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="cf796-150">Toto je dokument XML, jejichž kořenový element `<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="cf796-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="cf796-151">**Visual C#:** V **přidat novou položku** dialogového okna zvolte **soubor XML**.</span><span class="sxs-lookup"><span data-stu-id="cf796-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="cf796-152">Název tohoto souboru **app.config**. Po deklaraci XML v editoru XML, přidejte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="cf796-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="cf796-153">Při kompilaci projektu souboru app.config je zkopírován do výstupní složky projektu a přejmenování *applicationname*. exe.config.</span><span class="sxs-lookup"><span data-stu-id="cf796-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="cf796-154">Po `<configuration>` označit ale předtím, než `</configuration>` značky, přidejte odpovídající kód XML konfigurace vašeho přepínače.</span><span class="sxs-lookup"><span data-stu-id="cf796-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="cf796-155">Následující příklady ukazují **BooleanSwitch** s **DisplayName** vlastnost `DataMessageSwitch` a **TraceSwitch** s **DisplayName**  vlastnost `TraceLevelSwitch`.</span><span class="sxs-lookup"><span data-stu-id="cf796-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="cf796-156">V této konfiguraci jak přepínače jsou vypnuté.</span><span class="sxs-lookup"><span data-stu-id="cf796-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="cf796-157">Pokud je potřeba zapnout **BooleanSwitch**, jako `DataMessagesSwitch` je znázorněno v předchozím příkladu, změnit **hodnotu** libovolné celé číslo než 0.</span><span class="sxs-lookup"><span data-stu-id="cf796-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="cf796-158">Pokud je potřeba zapnout **TraceSwitch**, jako `TraceLevelSwitch` je znázorněno v předchozím příkladu, změnit **hodnotu** úrovně (1 až 4) nastavení.</span><span class="sxs-lookup"><span data-stu-id="cf796-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="cf796-159">Přidání komentářů do souboru .config, aby koncový uživatel má pochopili, jaké hodnoty chcete-li změnit konfiguraci přepínače odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="cf796-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="cf796-160">Následující příklad ukazuje, jak může vypadat konečný kód, komentáře, včetně:</span><span class="sxs-lookup"><span data-stu-id="cf796-160">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cf796-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf796-161">See also</span></span>

- [<span data-ttu-id="cf796-162">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="cf796-162">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="cf796-163">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="cf796-163">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="cf796-164">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="cf796-164">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="cf796-165">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="cf796-165">Trace and Debug Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
