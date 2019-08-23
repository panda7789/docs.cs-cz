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
ms.openlocfilehash: 9b1575d484c58afa3558d9f5b446473b4c89bc51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948001"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="5a1d7-102">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="5a1d7-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="5a1d7-103">Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="5a1d7-104">Vytvoření a inicializace přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="5a1d7-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="5a1d7-105">Aby bylo možné použít přepínače trasování, je nutné je nejprve vytvořit a umístit do kódu.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="5a1d7-106">Existují dvě předdefinované třídy, ze kterých lze vytvořit objekty Switch: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> třídu <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> a třídu.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5a1d7-107">Použili <xref:System.Diagnostics.BooleanSwitch> byste jenom v případě, že se zajímá jenom to, jestli se zobrazuje zpráva o trasování <xref:System.Diagnostics.TraceSwitch> . použijete, pokud chcete odlišit úroveň trasování.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="5a1d7-108">Pokud používáte <xref:System.Diagnostics.TraceSwitch>, můžete definovat vlastní zprávy pro ladění a přidružit je k různým úrovním trasování.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="5a1d7-109">Oba typy přepínačů lze použít buď pomocí trasování, nebo ladění.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="5a1d7-110">Ve výchozím nastavení <xref:System.Diagnostics.BooleanSwitch> je zakázána <xref:System.Diagnostics.TraceSwitch> a je nastavena na úroveň <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a1d7-111">Přepínače trasování lze vytvořit a umístit do jakékoli části kódu, který je může používat.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="5a1d7-112">I když můžete nastavit úrovně trasování a další možnosti konfigurace v kódu, doporučujeme, abyste ke správě stavu přepínačů použili konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="5a1d7-113">Důvodem je to, že Správa konfigurace přepínačů v konfiguračním systému poskytuje větší flexibilitu – můžete zapnout a vypnout různé přepínače a změnit úrovně bez nutnosti opětovné kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="5a1d7-114">Chcete-li vytvořit a inicializovat přepínač trasování</span><span class="sxs-lookup"><span data-stu-id="5a1d7-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="5a1d7-115">Definujte přepínač buď Type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> , nebo type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> a nastavte název a popis přepínače.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="5a1d7-116">Nakonfigurujte přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-116">Configure your trace switch.</span></span> <span data-ttu-id="5a1d7-117">Další informace najdete v tématu [konfigurace přepínačů trasování](#configure).</span><span class="sxs-lookup"><span data-stu-id="5a1d7-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="5a1d7-118">Následující kód vytvoří dva přepínače, jeden z každého typu:</span><span class="sxs-lookup"><span data-stu-id="5a1d7-118">The following code creates two switches, one of each type:</span></span>  
  
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
## <a name="configuring-trace-switches"></a><span data-ttu-id="5a1d7-119">Konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="5a1d7-119">Configuring trace switches</span></span>  
 <span data-ttu-id="5a1d7-120">Po distribuci aplikace můžete povolit nebo zakázat výstup trasování konfigurací přepínačů trasování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="5a1d7-121">Konfigurace přepínače znamená změnu hodnoty z externího zdroje poté, co byla inicializována.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="5a1d7-122">Hodnoty objektů Switch můžete změnit pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="5a1d7-123">Můžete nakonfigurovat přepínač trasování pro jeho zapnutí a vypnutí nebo pro nastavení jeho úrovně a určení množství a typu zpráv, které předává do posluchačů.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="5a1d7-124">Vaše přepínače jsou nakonfigurovány pomocí souboru. config.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="5a1d7-125">Pro webovou aplikaci je to soubor Web. config přidružený k projektu.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="5a1d7-126">V aplikaci pro Windows se tento soubor nazývá (název aplikace). exe. config. V nasazené aplikaci musí být tento soubor umístěn ve stejné složce jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="5a1d7-127">Když vaše aplikace spustí kód, který vytvoří instanci přepínače poprvé, zkontroluje konfigurační soubor o informace na úrovni trasování s pojmenovaným přepínačem.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="5a1d7-128">Systém trasování prověřuje konfigurační soubor pouze jednou pro konkrétní přepínač – při prvním vytvoření přepínače aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="5a1d7-129">V nasazené aplikaci povolíte trasovací kód tím, že překonfigurujete objekty přepínače, když vaše aplikace neběží.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="5a1d7-130">To obvykle zahrnuje zapnutí a vypnutí objektů přepínače nebo změnu úrovní trasování a následné restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="5a1d7-131">Když vytvoříte instanci přepínače, inicializujete ji také zadáním dvou argumentů: argumentu *DisplayName* a argumentem *Description* .</span><span class="sxs-lookup"><span data-stu-id="5a1d7-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="5a1d7-132">Argument *DisplayName* konstruktoru nastavuje <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> vlastnost <xref:System.Diagnostics.Switch> instance třídy.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="5a1d7-133">*DisplayName* je název, který se používá ke konfiguraci přepínače v souboru. config a argument *Description* by měl vracet stručný popis přepínače a o tom, které zprávy ovládací prvky IT.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="5a1d7-134">Kromě určení názvu přepínače, který se má nakonfigurovat, musíte zadat také hodnotu pro přepínač.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="5a1d7-135">Tato hodnota je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-135">This value is an Integer.</span></span> <span data-ttu-id="5a1d7-136">V případě hodnota 0 odpovídá **off**a jakákoli nenulová hodnota odpovídá **na.** <xref:System.Diagnostics.BooleanSwitch></span><span class="sxs-lookup"><span data-stu-id="5a1d7-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="5a1d7-137">U <xref:System.Diagnostics.TraceSwitch>, 0, 1, 2, 3 a 4 se shodují, **Chyba**, **Upozornění**, **informace**a **podrobné**, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="5a1d7-138">Jakékoli číslo, které je větší než 4, je považováno za **podrobné**a jakékoli číslo menší než nula je považováno za **vypnuto**.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a1d7-139">V .NET Framework verze 2,0 můžete použít text a zadat hodnotu pro přepínač.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="5a1d7-140">Například `true` `Error` pro nebo text představující<xref:System.Diagnostics.TraceSwitch>hodnotu výčtu, například pro. <xref:System.Diagnostics.BooleanSwitch></span><span class="sxs-lookup"><span data-stu-id="5a1d7-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="5a1d7-141">Čára `<add name="myTraceSwitch" value="Error" />` je`<add name="myTraceSwitch" value="1" />`ekvivalentem.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="5a1d7-142">Aby koncoví uživatelé mohli konfigurovat přepínače trasování aplikace, musíte poskytnout podrobnou dokumentaci k přepínačům ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="5a1d7-143">Měli byste si podrobně udělat, které přepínače řídí, co a jak je zapnout nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="5a1d7-144">Měli byste také poskytnout koncovému uživateli soubor. config, který má v komentářích odpovídající nápovědě.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="5a1d7-145">Konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="5a1d7-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="5a1d7-146">Aby bylo možné použít přepínače trasování, je nutné je nejprve vytvořit a umístit do kódu, jak je popsáno v části [Vytvoření a inicializace přepínače trasování](#create).</span><span class="sxs-lookup"><span data-stu-id="5a1d7-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="5a1d7-147">Pokud projekt neobsahuje konfigurační soubor (App. config nebo Web. config), pak v nabídce **projekt** vyberte možnost **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="5a1d7-148">**Visual Basic:** V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="5a1d7-149">Konfigurační soubor aplikace je vytvořen a otevřen.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="5a1d7-150">Toto je dokument XML, jehož kořenový element je`<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="5a1d7-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="5a1d7-151">**Vizuál C#:** V dialogovém okně **Přidat novou položku** vyberte **soubor XML**.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="5a1d7-152">Pojmenujte tento soubor **App. config**. V editoru XML po deklaraci XML přidejte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a1d7-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="5a1d7-153">Při kompilaci projektu se soubor App. config zkopíruje do výstupní složky projektu a přejmenuje se na soubor *ApplicationName*. exe. config.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="5a1d7-154">Po značce, ale před značku, přidejte odpovídající XML pro konfiguraci přepínačů. `</configuration>` `<configuration>`</span><span class="sxs-lookup"><span data-stu-id="5a1d7-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="5a1d7-155">Následující příklady znázorňují **BooleanSwitch** s `DataMessageSwitch` vlastností **DisplayName** a **TraceSwitch** s vlastností `TraceLevelSwitch` **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="5a1d7-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="5a1d7-156">V této konfiguraci jsou oba přepínače vypnuté.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="5a1d7-157">Pokud potřebujete zapnout **BooleanSwitch**, například `DataMessagesSwitch` znázorněné v předchozím příkladu, změňte **hodnotu** na celé číslo jiné než 0.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="5a1d7-158">Pokud potřebujete zapnout **TraceSwitch**, například `TraceLevelSwitch` v předchozím příkladu, změňte **hodnotu** na nastavení odpovídající úrovně (1 až 4).</span><span class="sxs-lookup"><span data-stu-id="5a1d7-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="5a1d7-159">Přidejte komentáře do souboru. config tak, aby měl koncový uživatel jasné porozumění hodnotám, které se mají změnit, a odpovídajícím způsobem nakonfigurovat přepínače.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="5a1d7-160">Následující příklad ukazuje, jak může vypadat konečný kód včetně komentářů.</span><span class="sxs-lookup"><span data-stu-id="5a1d7-160">The following example shows how the final code, including comments, might look:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a1d7-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a1d7-161">See also</span></span>

- [<span data-ttu-id="5a1d7-162">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="5a1d7-162">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="5a1d7-163">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="5a1d7-163">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="5a1d7-164">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="5a1d7-164">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="5a1d7-165">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="5a1d7-165">Trace and Debug Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
