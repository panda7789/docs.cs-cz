---
title: Vytváření vlastních součástí naslouchajících protokolům
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 5a140607a4fe7e1e13de54e8d56cab53e52aaa2a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398263"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="c0e12-102">Návod: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0e12-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="c0e12-103">Tento návod ukazuje, jak vytvořit vlastní naslouchací proces protokolu a nakonfigurovat ho tak, aby naslouchal výstupu `My.Application.Log` objektu.</span><span class="sxs-lookup"><span data-stu-id="c0e12-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="c0e12-104">začínáme</span><span class="sxs-lookup"><span data-stu-id="c0e12-104">Getting Started</span></span>

<span data-ttu-id="c0e12-105">Naslouchací procesy protokolu musí dědit od <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="c0e12-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="c0e12-106">Vytvoření naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="c0e12-106">To create the listener</span></span>

- <span data-ttu-id="c0e12-107">V aplikaci vytvořte třídu s názvem `SimpleListener` , která dědí z <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="c0e12-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="c0e12-108"><xref:System.Diagnostics.TraceListener.Write%2A>Metody a <xref:System.Diagnostics.TraceListener.WriteLine%2A> , které jsou požadovány pro základní třídu, volají `MsgBox` pro zobrazení jejich vstupu.</span><span class="sxs-lookup"><span data-stu-id="c0e12-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="c0e12-109"><xref:System.Security.Permissions.HostProtectionAttribute>Atribut se aplikuje na <xref:System.Diagnostics.TraceListener.Write%2A> metody a <xref:System.Diagnostics.TraceListener.WriteLine%2A> , aby jejich atributy odpovídaly metodám základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c0e12-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="c0e12-110"><xref:System.Security.Permissions.HostProtectionAttribute>Atribut umožňuje hostiteli, který spouští kód, určit, že kód zveřejňuje synchronizaci hostitele.</span><span class="sxs-lookup"><span data-stu-id="c0e12-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c0e12-111"><xref:System.Security.Permissions.HostProtectionAttribute>Atribut je platný pouze v nespravovaných aplikacích, které jsou hostiteli modulu CLR (Common Language Runtime) a které implementují ochranu hostitele, například SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0e12-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="c0e12-112">Chcete-li zajistit, aby `My.Application.Log` používala naslouchací proces protokolu, měli byste silně pojmenovat sestavení, které obsahuje váš naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="c0e12-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="c0e12-113">Další postup poskytuje několik jednoduchých kroků pro vytvoření silně pojmenovaného sestavení naslouchacího procesu protokolu.</span><span class="sxs-lookup"><span data-stu-id="c0e12-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="c0e12-114">Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="c0e12-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="c0e12-115">Pro silně pojmenování sestavení naslouchacího procesu protokolu</span><span class="sxs-lookup"><span data-stu-id="c0e12-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="c0e12-116">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="c0e12-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c0e12-117">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c0e12-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="c0e12-118">Klikněte na kartu **podepisování** .</span><span class="sxs-lookup"><span data-stu-id="c0e12-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="c0e12-119">Vyberte pole **podepsat sestavení** .</span><span class="sxs-lookup"><span data-stu-id="c0e12-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="c0e12-120">**\<New>** V rozevíracím seznamu vyberte **soubor klíče se silným názvem** vyberte.</span><span class="sxs-lookup"><span data-stu-id="c0e12-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="c0e12-121">Otevře se dialogové okno **vytvořit klíč se silným názvem** .</span><span class="sxs-lookup"><span data-stu-id="c0e12-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="c0e12-122">Zadejte název souboru klíče do pole **název souboru klíče** .</span><span class="sxs-lookup"><span data-stu-id="c0e12-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="c0e12-123">Do polí **Zadejte** heslo a **potvrďte heslo** zadejte heslo.</span><span class="sxs-lookup"><span data-stu-id="c0e12-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="c0e12-124">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0e12-124">Click **OK**.</span></span>

8. <span data-ttu-id="c0e12-125">Znovu sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c0e12-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="c0e12-126">Přidání naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="c0e12-126">Adding the Listener</span></span>

<span data-ttu-id="c0e12-127">Nyní, když má sestavení silný název, je nutné určit silný název naslouchacího procesu tak, aby `My.Application.Log` používal naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="c0e12-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="c0e12-128">Formát silně pojmenovaného typu je následující.</span><span class="sxs-lookup"><span data-stu-id="c0e12-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="c0e12-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span><span class="sxs-lookup"><span data-stu-id="c0e12-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="c0e12-130">Určení silného názvu naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="c0e12-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="c0e12-131">Následující kód ukazuje, jak určit název silně pojmenovaného typu pro `SimpleListener` .</span><span class="sxs-lookup"><span data-stu-id="c0e12-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="c0e12-132">Silný název typu závisí na vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="c0e12-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="c0e12-133">Se silným názvem můžete přidat naslouchací proces do `My.Application.Log` kolekce log-Listener.</span><span class="sxs-lookup"><span data-stu-id="c0e12-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="c0e12-134">Přidání naslouchacího procesu do My. Application. log</span><span class="sxs-lookup"><span data-stu-id="c0e12-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="c0e12-135">V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="c0e12-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="c0e12-136">-nebo-</span><span class="sxs-lookup"><span data-stu-id="c0e12-136">-or-</span></span>

     <span data-ttu-id="c0e12-137">Pokud existuje soubor App. config:</span><span class="sxs-lookup"><span data-stu-id="c0e12-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="c0e12-138">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="c0e12-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="c0e12-139">V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="c0e12-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="c0e12-140">Klikněte na tlačítko **Add** (Přidat).</span><span class="sxs-lookup"><span data-stu-id="c0e12-140">Click **Add**.</span></span>

2. <span data-ttu-id="c0e12-141">Vyhledejte `<listeners>` část v části `<source>` s `name` atributem "DefaultSource", který se nachází v `<sources>` části.</span><span class="sxs-lookup"><span data-stu-id="c0e12-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="c0e12-142">`<sources>`Oddíl je umístěný v části `<system.diagnostics>` v části nejvyšší úrovně `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="c0e12-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="c0e12-143">Přidejte tento element do `<listeners>` oddílu:</span><span class="sxs-lookup"><span data-stu-id="c0e12-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="c0e12-144">Vyhledejte část v části v `<sharedListeners>` `<system.diagnostics>` sekci nejvyšší úrovně `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="c0e12-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="c0e12-145">Přidejte tento element do této `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="c0e12-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="c0e12-146">Změňte hodnotu na se `SimpleLogStrongName` silným názvem naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="c0e12-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0e12-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0e12-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="c0e12-148">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="c0e12-148">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="c0e12-149">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="c0e12-149">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="c0e12-150">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="c0e12-150">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="c0e12-151">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="c0e12-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
