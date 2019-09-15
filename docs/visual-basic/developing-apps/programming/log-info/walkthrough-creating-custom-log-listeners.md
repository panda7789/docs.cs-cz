---
title: Vytváření vlastních protokolových posluchačů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: a4bd64d4c8232f9b6448baf98ee73ee497ccd5ca
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972112"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="f8cc6-102">Návod: Vytváření vlastních protokolových posluchačů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8cc6-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="f8cc6-103">Tento návod ukazuje, jak vytvořit vlastní naslouchací proces protokolu a nakonfigurovat ho tak, aby naslouchal výstupu `My.Application.Log` objektu.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="f8cc6-104">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f8cc6-104">Getting Started</span></span>  
 <span data-ttu-id="f8cc6-105">Naslouchací procesy protokolu musí dědit od <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="f8cc6-106">Vytvoření naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="f8cc6-106">To create the listener</span></span>  
  
- <span data-ttu-id="f8cc6-107">V aplikaci vytvořte třídu s názvem `SimpleListener` , která dědí z. <xref:System.Diagnostics.TraceListener></span><span class="sxs-lookup"><span data-stu-id="f8cc6-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <span data-ttu-id="f8cc6-108">Metody <xref:System.Diagnostics.TraceListener.Write%2A> `MsgBox` a <xref:System.Diagnostics.TraceListener.WriteLine%2A> , které jsou požadovány pro základní třídu, volají pro zobrazení jejich vstupu.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="f8cc6-109">Atribut se aplikuje <xref:System.Diagnostics.TraceListener.Write%2A> na metody a <xref:System.Diagnostics.TraceListener.WriteLine%2A> , aby jejich atributy odpovídaly metodám základní třídy. <xref:System.Security.Permissions.HostProtectionAttribute></span><span class="sxs-lookup"><span data-stu-id="f8cc6-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="f8cc6-110"><xref:System.Security.Permissions.HostProtectionAttribute> Atribut umožňuje hostiteli, který spouští kód, určit, že kód zveřejňuje synchronizaci hostitele.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f8cc6-111"><xref:System.Security.Permissions.HostProtectionAttribute> Atribut je platný pouze v nespravovaných aplikacích, které jsou hostiteli modulu CLR (Common Language Runtime) a které implementují ochranu hostitele, například SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="f8cc6-112">Chcete-li `My.Application.Log` zajistit, aby používala naslouchací proces protokolu, měli byste silně pojmenovat sestavení, které obsahuje váš naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="f8cc6-113">Další postup poskytuje několik jednoduchých kroků pro vytvoření silně pojmenovaného sestavení naslouchacího procesu protokolu.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="f8cc6-114">Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="f8cc6-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="f8cc6-115">Pro silně pojmenování sestavení naslouchacího procesu protokolu</span><span class="sxs-lookup"><span data-stu-id="f8cc6-115">To strongly name the log-listener assembly</span></span>  
  
1. <span data-ttu-id="f8cc6-116">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f8cc6-117">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2. <span data-ttu-id="f8cc6-118">Klikněte na kartu **podepisování** .</span><span class="sxs-lookup"><span data-stu-id="f8cc6-118">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="f8cc6-119">Vyberte pole **podepsat sestavení** .</span><span class="sxs-lookup"><span data-stu-id="f8cc6-119">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="f8cc6-120">V rozevíracím seznamu **Vyberte soubor klíče se silným názvem** vyberte  **\<nový >** .</span><span class="sxs-lookup"><span data-stu-id="f8cc6-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="f8cc6-121">Otevře se dialogové okno **vytvořit klíč se silným názvem** .</span><span class="sxs-lookup"><span data-stu-id="f8cc6-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5. <span data-ttu-id="f8cc6-122">Zadejte název souboru klíče do pole **název souboru klíče** .</span><span class="sxs-lookup"><span data-stu-id="f8cc6-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6. <span data-ttu-id="f8cc6-123">Do polí **Zadejte** heslo a **potvrďte heslo** zadejte heslo.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7. <span data-ttu-id="f8cc6-124">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-124">Click **OK**.</span></span>  
  
8. <span data-ttu-id="f8cc6-125">Znovu sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="f8cc6-126">Přidání naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="f8cc6-126">Adding the Listener</span></span>  
 <span data-ttu-id="f8cc6-127">Nyní, když má sestavení silný název, je nutné určit silný název naslouchacího procesu tak, `My.Application.Log` aby používal naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="f8cc6-128">Formát silně pojmenovaného typu je následující.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="f8cc6-129">\<název typu >, \<název sestavení >, \<číslo verze >, \<jazyková verze > \<, silný název ></span><span class="sxs-lookup"><span data-stu-id="f8cc6-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="f8cc6-130">Určení silného názvu naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="f8cc6-130">To determine the strong name of the listener</span></span>  
  
- <span data-ttu-id="f8cc6-131">Následující kód ukazuje, jak určit název silně pojmenovaného typu pro `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     <span data-ttu-id="f8cc6-132">Silný název typu závisí na vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="f8cc6-133">Se silným názvem můžete přidat naslouchací proces do `My.Application.Log` kolekce log-Listener.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="f8cc6-134">Přidání naslouchacího procesu do My. Application. log</span><span class="sxs-lookup"><span data-stu-id="f8cc6-134">To add the listener to My.Application.Log</span></span>  
  
1. <span data-ttu-id="f8cc6-135">V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="f8cc6-136">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f8cc6-136">-or-</span></span>  
  
     <span data-ttu-id="f8cc6-137">Pokud existuje soubor App. config:</span><span class="sxs-lookup"><span data-stu-id="f8cc6-137">If there is an app.config file:</span></span>  
  
    1. <span data-ttu-id="f8cc6-138">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="f8cc6-139">V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="f8cc6-140">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-140">Click **Add**.</span></span>  
  
2. <span data-ttu-id="f8cc6-141">Vyhledejte část v části s `name` atributem "DefaultSource", který se nachází v části.`<sources>` `<source>` `<listeners>`</span><span class="sxs-lookup"><span data-stu-id="f8cc6-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="f8cc6-142">Oddíl je umístěný `<system.diagnostics>` v části v části nejvyšší úrovně `<configuration>`. `<sources>`</span><span class="sxs-lookup"><span data-stu-id="f8cc6-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="f8cc6-143">Přidejte tento element do `<listeners>` oddílu:</span><span class="sxs-lookup"><span data-stu-id="f8cc6-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. <span data-ttu-id="f8cc6-144">`<sharedListeners>` Vyhledejte část `<system.diagnostics>` v části v sekci nejvyšší úrovně `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="f8cc6-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="f8cc6-145">Přidejte tento element do této `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="f8cc6-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="f8cc6-146">Změňte hodnotu `SimpleLogStrongName` na se silným názvem naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="f8cc6-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8cc6-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8cc6-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="f8cc6-148">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="f8cc6-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="f8cc6-149">Postupy: Protokolovat výjimky</span><span class="sxs-lookup"><span data-stu-id="f8cc6-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="f8cc6-150">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="f8cc6-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="f8cc6-151">Návod: Změna místa, kam aplikace My. Application. Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="f8cc6-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
