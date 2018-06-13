---
title: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 6139a1fef2b2c37bc2c8a6167febd060d8d01fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591648"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="676e3-102">Návod: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="676e3-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="676e3-103">Tento návod ukazuje, jak vytvořit vlastní protokol naslouchací proces a nakonfigurovat ji tak, aby naslouchala na výstupu `My.Application.Log` objektu.</span><span class="sxs-lookup"><span data-stu-id="676e3-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="676e3-104">Začínáme</span><span class="sxs-lookup"><span data-stu-id="676e3-104">Getting Started</span></span>  
 <span data-ttu-id="676e3-105">Naslouchací procesy pro protokoly musí dědit z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="676e3-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="676e3-106">Chcete-li vytvořit naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="676e3-106">To create the listener</span></span>  
  
-   <span data-ttu-id="676e3-107">V aplikaci, vytvořte třídu s názvem `SimpleListener` který dědí z <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="676e3-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <span data-ttu-id="676e3-108"><xref:System.Diagnostics.TraceListener.Write%2A> a <xref:System.Diagnostics.TraceListener.WriteLine%2A> volání metody, které vyžadují základní třídy, `MsgBox` pro zobrazení jejich vstupu.</span><span class="sxs-lookup"><span data-stu-id="676e3-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="676e3-109"><xref:System.Security.Permissions.HostProtectionAttribute> Je použit atribut <xref:System.Diagnostics.TraceListener.Write%2A> a <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody tak, aby odpovídaly metody třídy base jejich atributy.</span><span class="sxs-lookup"><span data-stu-id="676e3-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="676e3-110"><xref:System.Security.Permissions.HostProtectionAttribute> Atribut umožňuje hostiteli, který spouští kód, určit, zda kód zpřístupňuje hostitelskou ochranu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="676e3-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="676e3-111"><xref:System.Security.Permissions.HostProtectionAttribute> Atribut je platná pouze v nespravovaných aplikacích, které jsou hostiteli modul common language runtime a které implementují ochrany hostitele, jako je SQL Server.</span><span class="sxs-lookup"><span data-stu-id="676e3-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="676e3-112">Zajistit, aby `My.Application.Log` používá vaše naslouchací proces protokolu důrazně by měl název sestavení, které obsahuje váš naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="676e3-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="676e3-113">Následující postup poskytuje několika jednoduchých kroků pro vytvoření silně pojmenované naslouchací proces protokolu sestavení.</span><span class="sxs-lookup"><span data-stu-id="676e3-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="676e3-114">Další informace najdete v tématu [vytvoření a použití sestavení](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="676e3-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="676e3-115">Důrazně název naslouchacího procesu protokolu sestavení</span><span class="sxs-lookup"><span data-stu-id="676e3-115">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="676e3-116">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="676e3-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="676e3-117">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="676e3-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2.  <span data-ttu-id="676e3-118">Klikněte **podpisování** kartě.</span><span class="sxs-lookup"><span data-stu-id="676e3-118">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="676e3-119">Vyberte **podepsání sestavení** pole.</span><span class="sxs-lookup"><span data-stu-id="676e3-119">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="676e3-120">Vyberte  **\<nový >** z **vyberte soubor klíče se silným názvem** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="676e3-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="676e3-121">**Vytvořit klíč se silným názvem** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="676e3-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="676e3-122">Zadejte název souboru klíče v **název souboru klíče** pole.</span><span class="sxs-lookup"><span data-stu-id="676e3-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="676e3-123">Zadejte heslo do **zadejte heslo** a **potvrzení hesla** polí.</span><span class="sxs-lookup"><span data-stu-id="676e3-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="676e3-124">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="676e3-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="676e3-125">Znovu sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="676e3-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="676e3-126">Přidání naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="676e3-126">Adding the Listener</span></span>  
 <span data-ttu-id="676e3-127">Nyní, když sestavení silným názvem, budete muset určit silný název naslouchacího procesu tak, aby `My.Application.Log` používá vaše naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="676e3-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="676e3-128">Formát silně pojmenovaného typu je následující.</span><span class="sxs-lookup"><span data-stu-id="676e3-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="676e3-129">\<Název typu >, \<název sestavení >, \<číslo verze >, \<culture >, \<silné jméno ></span><span class="sxs-lookup"><span data-stu-id="676e3-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="676e3-130">Chcete-li určit silný název naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="676e3-130">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="676e3-131">Následující kód ukazuje, jak určit název silně pojmenovaného typu pro `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="676e3-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     <span data-ttu-id="676e3-132">Silný název typu závisí na projektu.</span><span class="sxs-lookup"><span data-stu-id="676e3-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="676e3-133">Se silným názvem, můžete přidat naslouchacího procesu `My.Application.Log` naslouchání protokolu kolekce.</span><span class="sxs-lookup"><span data-stu-id="676e3-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="676e3-134">Chcete-li přidat naslouchací proces pro My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="676e3-134">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="676e3-135">Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="676e3-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="676e3-136">-nebo-</span><span class="sxs-lookup"><span data-stu-id="676e3-136">-or-</span></span>  
  
     <span data-ttu-id="676e3-137">Pokud je soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="676e3-137">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="676e3-138">Na **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="676e3-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="676e3-139">Z **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="676e3-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="676e3-140">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="676e3-140">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="676e3-141">Vyhledejte `<listeners>` v části `<source>` část s `name` atributu "DefaultSource", umístěný ve `<sources>` části.</span><span class="sxs-lookup"><span data-stu-id="676e3-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="676e3-142">`<sources>` Je umístěna v `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="676e3-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="676e3-143">Přidejte tento element na `<listeners>` části:</span><span class="sxs-lookup"><span data-stu-id="676e3-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="676e3-144">Vyhledejte `<sharedListeners>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="676e3-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="676e3-145">Přidejte tento element do `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="676e3-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="676e3-146">Změňte hodnotu `SimpleLogStrongName` jako silný název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="676e3-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="676e3-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="676e3-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="676e3-148">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="676e3-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="676e3-149">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="676e3-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="676e3-150">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="676e3-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="676e3-151">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="676e3-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
