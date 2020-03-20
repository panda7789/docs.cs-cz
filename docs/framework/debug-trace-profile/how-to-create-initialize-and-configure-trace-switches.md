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
ms.openlocfilehash: 8bf3b974ff0ef9f719274ab684b3dce85295c917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181830"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="9b941-102">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="9b941-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="9b941-103">Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="9b941-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="9b941-104">Vytvoření a inicializace přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="9b941-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="9b941-105">Chcete-li použít přepínače trasování, musíte je nejprve vytvořit a umístit do kódu.</span><span class="sxs-lookup"><span data-stu-id="9b941-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="9b941-106">Existují dvě předdefinované třídy, ze kterých <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> můžete <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> vytvořit objekty přepínače: třída a třída.</span><span class="sxs-lookup"><span data-stu-id="9b941-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9b941-107">Použili <xref:System.Diagnostics.BooleanSwitch> byste, pokud vám záleží pouze na tom, zda se zobrazí zpráva o trasování; které byste <xref:System.Diagnostics.TraceSwitch> použili, pokud chcete rozlišovat mezi úrovněmi trasování.</span><span class="sxs-lookup"><span data-stu-id="9b941-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="9b941-108">Pokud používáte <xref:System.Diagnostics.TraceSwitch>, můžete definovat vlastní ladicí zprávy a přidružit je k různým úrovním trasování.</span><span class="sxs-lookup"><span data-stu-id="9b941-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="9b941-109">Oba typy přepínačů můžete použít s trasováním nebo laděním.</span><span class="sxs-lookup"><span data-stu-id="9b941-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="9b941-110">Ve výchozím <xref:System.Diagnostics.BooleanSwitch> nastavení je <xref:System.Diagnostics.TraceSwitch> a zakázána <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>a je nastavena na úroveň .</span><span class="sxs-lookup"><span data-stu-id="9b941-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9b941-111">Přepínače trasování lze vytvořit a umístit do libovolné části kódu, který je může používat.</span><span class="sxs-lookup"><span data-stu-id="9b941-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="9b941-112">Přestože můžete nastavit úrovně trasování a další možnosti konfigurace v kódu, doporučujeme použít konfigurační soubor ke správě stavu přepínačů.</span><span class="sxs-lookup"><span data-stu-id="9b941-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="9b941-113">Je to proto, že správa konfigurace přepínačů v konfiguračním systému poskytuje větší flexibilitu – můžete zapnout a vypnout různé přepínače a změnit úrovně bez nutnosti opětovné kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b941-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="9b941-114">Vytvoření a inicializaci přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="9b941-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="9b941-115">Definujte přepínač jako <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> nebo typ a nastavte název a popis přepínače.</span><span class="sxs-lookup"><span data-stu-id="9b941-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="9b941-116">Nakonfigurujte přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="9b941-116">Configure your trace switch.</span></span> <span data-ttu-id="9b941-117">Další informace naleznete [v tématu Konfigurace přepínačů trasování](#configure).</span><span class="sxs-lookup"><span data-stu-id="9b941-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="9b941-118">Následující kód vytvoří dva přepínače, jeden z každého typu:</span><span class="sxs-lookup"><span data-stu-id="9b941-118">The following code creates two switches, one of each type:</span></span>  
  
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
## <a name="configuring-trace-switches"></a><span data-ttu-id="9b941-119">Konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="9b941-119">Configuring trace switches</span></span>  
 <span data-ttu-id="9b941-120">Po distribuci aplikace můžete stále povolit nebo zakázat výstup trasování konfigurací trasovacích přepínačů v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9b941-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="9b941-121">Konfigurace přepínače znamená změnu jeho hodnoty z externího zdroje po jeho inicializací.</span><span class="sxs-lookup"><span data-stu-id="9b941-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="9b941-122">Pomocí konfiguračního souboru můžete změnit hodnoty objektů přepínače.</span><span class="sxs-lookup"><span data-stu-id="9b941-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="9b941-123">Nakonfigurujete přepínač trasování, abyste jej zapínali a vypínali nebo nastavili jeho úroveň a určili množství a typ zpráv, které předává posluchačům.</span><span class="sxs-lookup"><span data-stu-id="9b941-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="9b941-124">Přepínače jsou konfigurovány pomocí souboru .config.</span><span class="sxs-lookup"><span data-stu-id="9b941-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="9b941-125">Pro webovou aplikaci se jedná o soubor Web.config přidružený k projektu.</span><span class="sxs-lookup"><span data-stu-id="9b941-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="9b941-126">V aplikaci systému Windows je tento soubor pojmenován (název aplikace).exe.config. V nasazené aplikaci musí být tento soubor umístěn ve stejné složce jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="9b941-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="9b941-127">Když aplikace spustí kód, který vytvoří instanci přepínače poprvé, zkontroluje konfigurační soubor informace o úrovni trasování o pojmenované přepínači.</span><span class="sxs-lookup"><span data-stu-id="9b941-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="9b941-128">Systém trasování zkontroluje konfigurační soubor pouze jednou pro konkrétní přepínač – při prvním spuštění aplikace přepínač.</span><span class="sxs-lookup"><span data-stu-id="9b941-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="9b941-129">V nasazené aplikaci povolíte trasovací kód změnou konfigurace objektů přepínače, když vaše aplikace není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9b941-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="9b941-130">Obvykle to zahrnuje zapnutí a vypnutí objektů přepínače nebo změnou úrovní trasování a restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b941-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="9b941-131">Když vytvoříte instanci přepínače, inicializujete ji také zadáním dvou argumentů: argumentu *displayName* a argumentu *popisu.*</span><span class="sxs-lookup"><span data-stu-id="9b941-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="9b941-132">Argument *displayName* konstruktoru <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> nastaví vlastnost <xref:System.Diagnostics.Switch> instance třídy.</span><span class="sxs-lookup"><span data-stu-id="9b941-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="9b941-133">*DisplayName* je název, který se používá ke konfiguraci přepínače v souboru .config a argument *description* by měl vrátit stručný popis přepínače a zpráv, které řídí.</span><span class="sxs-lookup"><span data-stu-id="9b941-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="9b941-134">Kromě zadání názvu přepínače ke konfiguraci je nutné zadat také hodnotu přepínače.</span><span class="sxs-lookup"><span data-stu-id="9b941-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="9b941-135">Tato hodnota je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9b941-135">This value is an Integer.</span></span> <span data-ttu-id="9b941-136">Pro <xref:System.Diagnostics.BooleanSwitch>hodnota 0 odpovídá **Off**a jakákoli nenulová hodnota odpovídá **On**.</span><span class="sxs-lookup"><span data-stu-id="9b941-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="9b941-137">Pro <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3 a 4 odpovídají **Off**, **Error**, **Warning**, **Info**a **Verbose**, resp.</span><span class="sxs-lookup"><span data-stu-id="9b941-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="9b941-138">Jakékoli číslo větší než 4 je považováno za **podrobné**a jakékoli číslo menší než nula je považováno za **Off**.</span><span class="sxs-lookup"><span data-stu-id="9b941-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b941-139">V rozhraní .NET Framework verze 2.0 můžete použít text k určení hodnoty přepínače.</span><span class="sxs-lookup"><span data-stu-id="9b941-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="9b941-140">Například `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo text představující hodnotu výčtu, <xref:System.Diagnostics.TraceSwitch>například `Error` pro .</span><span class="sxs-lookup"><span data-stu-id="9b941-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="9b941-141">Řádek `<add name="myTraceSwitch" value="Error" />` je ekvivalentní `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="9b941-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="9b941-142">Aby koncoví uživatelé mohli konfigurovat trasovací přepínače aplikace, musíte poskytnout podrobnou dokumentaci o přepínačích ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9b941-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="9b941-143">Měli byste podrobně popsat, které přepínače řídí, co a jak je zapínat a vypínat.</span><span class="sxs-lookup"><span data-stu-id="9b941-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="9b941-144">Měli byste také poskytnout koncovému uživateli soubor .config, který má příslušnou nápovědu v komentářích.</span><span class="sxs-lookup"><span data-stu-id="9b941-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="9b941-145">Konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="9b941-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="9b941-146">Chcete-li použít přepínače trasování, musíte je nejprve vytvořit a umístit do kódu, jak je popsáno v části [Vytvoření a inicializace přepínače trasování](#create).</span><span class="sxs-lookup"><span data-stu-id="9b941-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="9b941-147">Pokud projekt neobsahuje konfigurační soubor (app.config nebo Web.config), pak z nabídky **Projekt** vyberte **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="9b941-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="9b941-148">**Visual Basic:** V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="9b941-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="9b941-149">Konfigurační soubor aplikace je vytvořen a otevřen.</span><span class="sxs-lookup"><span data-stu-id="9b941-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="9b941-150">Jedná se o dokument XML, jehož kořenový prvek je`<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="9b941-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="9b941-151">**Vizuální jazyk C#:** V dialogovém okně **Přidat novou položku** zvolte **Soubor XML**.</span><span class="sxs-lookup"><span data-stu-id="9b941-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="9b941-152">Pojmenujte tento soubor **app.config**. V editoru XML přidejte za deklaraci XML následující XML:</span><span class="sxs-lookup"><span data-stu-id="9b941-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="9b941-153">Při kompilaci projektu je soubor app.config zkopírován do výstupní složky projektu a přejmenován *na název_aplikace*.exe.config.</span><span class="sxs-lookup"><span data-stu-id="9b941-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="9b941-154">Za `<configuration>` značku, ale `</configuration>` před značku, přidejte příslušný XML pro konfiguraci přepínačů.</span><span class="sxs-lookup"><span data-stu-id="9b941-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="9b941-155">Následující příklady ukazují **BooleanSwitch** s Vlastnost `DataMessageSwitch` **DisplayName** a **TraceSwitch** s `TraceLevelSwitch` **DisplayName** vlastnost .</span><span class="sxs-lookup"><span data-stu-id="9b941-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="9b941-156">V této konfiguraci jsou oba přepínače vypnuty.</span><span class="sxs-lookup"><span data-stu-id="9b941-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="9b941-157">Pokud potřebujete zapnout **Přepínač BooleanSwitch** `DataMessagesSwitch` , jak je znázorněno v předchozím příkladu, změňte **hodnotu** na libovolné celé číslo než 0.</span><span class="sxs-lookup"><span data-stu-id="9b941-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="9b941-158">Pokud potřebujete zapnout **TraceSwitch**, `TraceLevelSwitch` jak je znázorněno v předchozím příkladu, změňte **hodnotu** na příslušnou úroveň nastavení (1 až 4).</span><span class="sxs-lookup"><span data-stu-id="9b941-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="9b941-159">Přidejte komentáře do souboru .config, aby koncový uživatel měl jasnou představu o tom, jaké hodnoty změnit pro vhodnou konfiguraci přepínačů.</span><span class="sxs-lookup"><span data-stu-id="9b941-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="9b941-160">Následující příklad ukazuje, jak může vypadat konečný kód, včetně komentářů:</span><span class="sxs-lookup"><span data-stu-id="9b941-160">The following example shows how the final code, including comments, might look:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b941-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b941-161">See also</span></span>

- [<span data-ttu-id="9b941-162">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="9b941-162">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="9b941-163">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="9b941-163">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="9b941-164">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="9b941-164">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="9b941-165">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="9b941-165">Trace and Debug Settings Schema</span></span>](../configure-apps/file-schema/trace-debug/index.md)
