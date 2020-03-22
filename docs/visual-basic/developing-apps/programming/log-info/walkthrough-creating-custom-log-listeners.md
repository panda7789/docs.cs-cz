---
title: Vytváření vlastních součástí naslouchajících protokolům
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353613"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="987fe-102">Návod: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="987fe-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="987fe-103">Tento návod ukazuje, jak vytvořit vlastní naslouchací proces `My.Application.Log` protokolu a nakonfigurovat jej tak, aby poslouchat výstup objektu.</span><span class="sxs-lookup"><span data-stu-id="987fe-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="987fe-104">Začínáme</span><span class="sxs-lookup"><span data-stu-id="987fe-104">Getting Started</span></span>

<span data-ttu-id="987fe-105">Posluchači protokolu musí <xref:System.Diagnostics.TraceListener> dědit z třídy.</span><span class="sxs-lookup"><span data-stu-id="987fe-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="987fe-106">Vytvoření naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="987fe-106">To create the listener</span></span>

- <span data-ttu-id="987fe-107">V aplikaci vytvořte `SimpleListener` třídu s <xref:System.Diagnostics.TraceListener>názvem, která dědí z .</span><span class="sxs-lookup"><span data-stu-id="987fe-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="987fe-108">Metody <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> a vyžadované `MsgBox` základní třídou volají k zobrazení jejich vstupu.</span><span class="sxs-lookup"><span data-stu-id="987fe-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="987fe-109">Atribut <xref:System.Security.Permissions.HostProtectionAttribute> je použit <xref:System.Diagnostics.TraceListener.Write%2A> na <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody a tak, aby jejich atributy odpovídaly metodám základní třídy.</span><span class="sxs-lookup"><span data-stu-id="987fe-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="987fe-110">Atribut <xref:System.Security.Permissions.HostProtectionAttribute> umožňuje hostiteli, který spouští kód k určení, že kód zveřejňuje synchronizaci ochrany hostitele.</span><span class="sxs-lookup"><span data-stu-id="987fe-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="987fe-111">Atribut <xref:System.Security.Permissions.HostProtectionAttribute> je účinný pouze u nespravovaných aplikací, které hostují modul runtime společného jazyka a které implementují ochranu hostitele, například SQL Server.</span><span class="sxs-lookup"><span data-stu-id="987fe-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="987fe-112">Chcete-li `My.Application.Log` zajistit, že používá naslouchací proces protokolu, měli byste důrazně pojmenovat sestavení, které obsahuje naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="987fe-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="987fe-113">Další postup poskytuje některé jednoduché kroky pro vytvoření sestavení silně pojmenované protokol naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="987fe-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="987fe-114">Další informace naleznete v [tématu Vytváření a používání sestavení se silným názvem](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="987fe-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="987fe-115">Silně pojmenovat sestavení posluchače protokolu</span><span class="sxs-lookup"><span data-stu-id="987fe-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="987fe-116">V **Průzkumníku řešení**je vybrán projekt .</span><span class="sxs-lookup"><span data-stu-id="987fe-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="987fe-117">V nabídce **Projekt** zvolte **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="987fe-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="987fe-118">Klikněte na kartu **Podpis.**</span><span class="sxs-lookup"><span data-stu-id="987fe-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="987fe-119">Vyberte podepsat pole **sestavy.**</span><span class="sxs-lookup"><span data-stu-id="987fe-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="987fe-120">V \*\* \<\*\* rozevíracím seznamu Zvolte Nový>v rozevíracím seznamu **Zvolit soubor klíče silného názvu.**</span><span class="sxs-lookup"><span data-stu-id="987fe-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="987fe-121">Otevře se dialogové okno **Vytvořit klíč silného názvu.**</span><span class="sxs-lookup"><span data-stu-id="987fe-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="987fe-122">Zadejte název souboru klíče do pole **Název souboru klíče.**</span><span class="sxs-lookup"><span data-stu-id="987fe-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="987fe-123">Zadejte heslo do polí **Zadat heslo** a **Potvrdit heslo.**</span><span class="sxs-lookup"><span data-stu-id="987fe-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="987fe-124">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="987fe-124">Click **OK**.</span></span>

8. <span data-ttu-id="987fe-125">Znovu sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="987fe-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="987fe-126">Přidání naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="987fe-126">Adding the Listener</span></span>

<span data-ttu-id="987fe-127">Nyní, když sestavení má silný název, je třeba určit silný `My.Application.Log` název naslouchací proces tak, že používá posluchače protokolu.</span><span class="sxs-lookup"><span data-stu-id="987fe-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="987fe-128">Formát silně pojmenovaného typu je následující.</span><span class="sxs-lookup"><span data-stu-id="987fe-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="987fe-129">\<název>, \<název sestavení \<>, \<číslo verze \<>,> jazykové verze,></span><span class="sxs-lookup"><span data-stu-id="987fe-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="987fe-130">Chcete-li určit silný název naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="987fe-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="987fe-131">Následující kód ukazuje, jak určit silně pojmenovaný `SimpleListener`název typu pro .</span><span class="sxs-lookup"><span data-stu-id="987fe-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="987fe-132">Silný název typu závisí na projektu.</span><span class="sxs-lookup"><span data-stu-id="987fe-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="987fe-133">S silným názvem můžete přidat naslouchací proces do kolekce naslouchací `My.Application.Log` proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="987fe-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="987fe-134">Přidání naslouchací proces do My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="987fe-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="987fe-135">Klikněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.</span><span class="sxs-lookup"><span data-stu-id="987fe-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="987fe-136">-nebo-</span><span class="sxs-lookup"><span data-stu-id="987fe-136">-or-</span></span>

     <span data-ttu-id="987fe-137">Pokud existuje soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="987fe-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="987fe-138">V nabídce **Projekt** zvolte **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="987fe-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="987fe-139">V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="987fe-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="987fe-140">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="987fe-140">Click **Add**.</span></span>

2. <span data-ttu-id="987fe-141">Vyhledejte `<listeners>` oddíl v `<source>` části `name` s atributem "DefaultSource", který se nachází v `<sources>` sekci.</span><span class="sxs-lookup"><span data-stu-id="987fe-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="987fe-142">Sekce `<sources>` je umístěna `<system.diagnostics>` v sekci, v `<configuration>` sekci nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="987fe-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="987fe-143">Přidejte tento `<listeners>` prvek do oddílu:</span><span class="sxs-lookup"><span data-stu-id="987fe-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="987fe-144">Vyhledejte `<sharedListeners>` oddíl v `<system.diagnostics>` části v části `<configuration>` nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="987fe-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="987fe-145">Přidejte tento `<sharedListeners>` prvek do tohoto oddílu:</span><span class="sxs-lookup"><span data-stu-id="987fe-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="987fe-146">Změňte hodnotu `SimpleLogStrongName` má být silný název naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="987fe-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="987fe-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="987fe-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="987fe-148">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="987fe-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="987fe-149">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="987fe-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="987fe-150">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="987fe-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="987fe-151">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="987fe-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
