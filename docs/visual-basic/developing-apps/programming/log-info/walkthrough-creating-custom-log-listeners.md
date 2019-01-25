---
title: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 12943e449f825516d37079e7ddac2a6705879066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710505"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="ecbb6-102">Průvodce: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecbb6-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="ecbb6-103">Tento návod ukazuje, jak vytvořit vlastní protokol naslouchací proces a nakonfigurujte ho tak, aby naslouchala na výstupu `My.Application.Log` objektu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="ecbb6-104">Začínáme</span><span class="sxs-lookup"><span data-stu-id="ecbb6-104">Getting Started</span></span>  
 <span data-ttu-id="ecbb6-105">Součásti naslouchající protokolům musí dědit z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="ecbb6-106">Chcete-li vytvořit naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="ecbb6-106">To create the listener</span></span>  
  
-   <span data-ttu-id="ecbb6-107">Ve vaší aplikaci, vytvořte třídu s názvem `SimpleListener` , která dědí z <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <span data-ttu-id="ecbb6-108"><xref:System.Diagnostics.TraceListener.Write%2A> a <xref:System.Diagnostics.TraceListener.WriteLine%2A> volání metody základní třídy, vyžaduje `MsgBox` zobrazíte svůj vstup.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="ecbb6-109"><xref:System.Security.Permissions.HostProtectionAttribute> Atribut aplikován <xref:System.Diagnostics.TraceListener.Write%2A> a <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody tak, aby jejich atributy odpovídají metody základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="ecbb6-110"><xref:System.Security.Permissions.HostProtectionAttribute> Atribut umožňuje hostiteli, který spouští kód určující, že kód poskytuje ochranu hostitel synchronizace.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecbb6-111"><xref:System.Security.Permissions.HostProtectionAttribute> Atribut je platná pouze v nespravovaných aplikacích, které jsou hostiteli modulu common language runtime a, které implementují ochranu hostitele, jako je SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="ecbb6-112">Chcete-li zajistit `My.Application.Log` používá vaše naslouchací proces protokolu důrazně by měl název sestavení, které obsahuje váš protokol naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="ecbb6-113">Následující postup obsahuje několika jednoduchými kroky pro vytvoření sestavení silným názvem naslouchacího procesu protokolu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="ecbb6-114">Další informace najdete v tématu [vytvoření a použití sestavení](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ecbb6-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="ecbb6-115">Důrazně název naslouchacího procesu protokolu sestavení</span><span class="sxs-lookup"><span data-stu-id="ecbb6-115">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="ecbb6-116">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ecbb6-117">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2.  <span data-ttu-id="ecbb6-118">Klikněte na tlačítko **podepisování** kartu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-118">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="ecbb6-119">Vyberte **podepsat sestavení** pole.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-119">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="ecbb6-120">Vyberte  **\<nový >** z **vyberte soubor klíče se silným názvem** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="ecbb6-121">**Vytvořit klíč se silným názvem** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="ecbb6-122">Zadejte název souboru klíče **název souboru klíče** pole.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="ecbb6-123">Zadejte heslo **zadejte heslo** a **potvrzení hesla** polí.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="ecbb6-124">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="ecbb6-125">Znovu sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="ecbb6-126">Přidání posluchače</span><span class="sxs-lookup"><span data-stu-id="ecbb6-126">Adding the Listener</span></span>  
 <span data-ttu-id="ecbb6-127">Teď, když sestavení se silným názvem, budete muset určit silný název naslouchacího procesu tak, aby `My.Application.Log` používá vašemu naslouchacímu procesu protokolu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="ecbb6-128">Formát typu silným názvem je následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="ecbb6-129">\<Název typu >, \<název sestavení >, \<číslo verze >, \<jazykové verze >, \<silného názvu ></span><span class="sxs-lookup"><span data-stu-id="ecbb6-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="ecbb6-130">Chcete-li zjistit silný název naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="ecbb6-130">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="ecbb6-131">Následující kód ukazuje, jak určit název silným názvem typu `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     <span data-ttu-id="ecbb6-132">Silný název typu závisí na vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="ecbb6-133">Se silným názvem, můžete přidat posluchače `My.Application.Log` shromažďování protokolů naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="ecbb6-134">Chcete-li přidat naslouchací proces pro My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="ecbb6-134">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="ecbb6-135">Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a zvolte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="ecbb6-136">-nebo-</span><span class="sxs-lookup"><span data-stu-id="ecbb6-136">-or-</span></span>  
  
     <span data-ttu-id="ecbb6-137">Pokud je soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="ecbb6-137">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="ecbb6-138">Na **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="ecbb6-139">Z **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="ecbb6-140">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-140">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="ecbb6-141">Vyhledejte `<listeners>` sekci `<source>` části s `name` atribut "DefaultSource" v `<sources>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="ecbb6-142">`<sources>` Je umístěna v `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="ecbb6-143">Přidání tohoto elementu `<listeners>` části:</span><span class="sxs-lookup"><span data-stu-id="ecbb6-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="ecbb6-144">Vyhledejte `<sharedListeners>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="ecbb6-145">Přidejte tento element, který `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="ecbb6-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="ecbb6-146">Změňte hodnotu vlastnosti `SimpleLogStrongName` silný název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="ecbb6-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbb6-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecbb6-147">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="ecbb6-148">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="ecbb6-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="ecbb6-149">Postupy: Výjimky protokolu</span><span class="sxs-lookup"><span data-stu-id="ecbb6-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="ecbb6-150">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="ecbb6-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="ecbb6-151">Návod: Změna, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="ecbb6-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
