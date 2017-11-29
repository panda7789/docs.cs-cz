---
title: "Přepínače trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 082d84fe0ac4193f3da5ac9be52789432bde76aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="trace-switches"></a><span data-ttu-id="b89c6-102">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="b89c6-102">Trace Switches</span></span>
<span data-ttu-id="b89c6-103">Trasování – přepínače umožňují povolit, zakázat a filtrovat výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="b89c6-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span> <span data-ttu-id="b89c6-104">Jsou objekty, které existují ve vašem kódu a možné externě nakonfigurovat pomocí souboru .config.</span><span class="sxs-lookup"><span data-stu-id="b89c6-104">They are objects that exist in your code and can be configured externally through the .config file.</span></span> <span data-ttu-id="b89c6-105">Existují tři typy trasování – přepínače zadaný v rozhraní .NET Framework: <xref:System.Diagnostics.BooleanSwitch> třídy, <xref:System.Diagnostics.TraceSwitch> třída a <xref:System.Diagnostics.SourceSwitch> třídy.</span><span class="sxs-lookup"><span data-stu-id="b89c6-105">There are three types of trace switches provided in the .NET Framework: the <xref:System.Diagnostics.BooleanSwitch> class, the <xref:System.Diagnostics.TraceSwitch> class, and the <xref:System.Diagnostics.SourceSwitch> class.</span></span> <span data-ttu-id="b89c6-106"><xref:System.Diagnostics.BooleanSwitch> Třída slouží jako přepínač přepnutí, povolení nebo zakázání celou řadu příkazů trasování.</span><span class="sxs-lookup"><span data-stu-id="b89c6-106">The <xref:System.Diagnostics.BooleanSwitch> class acts as a toggle switch, either enabling or disabling a variety of trace statements.</span></span> <span data-ttu-id="b89c6-107"><xref:System.Diagnostics.TraceSwitch> a <xref:System.Diagnostics.SourceSwitch> třídy možné povolit přepínače trasování pro konkrétní trasování úroveň tak, aby <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.TraceSource> zadané pro tuto úroveň a nižší úrovně všechny zprávy se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="b89c6-107">The <xref:System.Diagnostics.TraceSwitch> and <xref:System.Diagnostics.SourceSwitch> classes allow you to enable a trace switch for a particular tracing level so that the <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.TraceSource> messages specified for that level and all levels below it appear.</span></span> <span data-ttu-id="b89c6-108">Pokud zakážete přepínač, nebude se zobrazovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="b89c6-108">If you disable the switch, the trace messages will not appear.</span></span> <span data-ttu-id="b89c6-109">Všechny tyto třídy jsou odvozeny od abstraktní (**MustInherit**) třídy **přepínač**, jako by všechny uživatele vyvinuté přepínače.</span><span class="sxs-lookup"><span data-stu-id="b89c6-109">All these classes derive from the abstract (**MustInherit**) class **Switch**, as should any user-developed switches.</span></span>  
  
 <span data-ttu-id="b89c6-110">Trasování – přepínače může být užitečná pro filtrování informací.</span><span class="sxs-lookup"><span data-stu-id="b89c6-110">Trace switches can be useful for filtering information.</span></span> <span data-ttu-id="b89c6-111">Například můžete chtít zobrazit všechny zprávy trasování v modulu přístupu k datům, ale pouze chybové zprávy ve zbývající části aplikace.</span><span class="sxs-lookup"><span data-stu-id="b89c6-111">For example, you might want to see every tracing message in a data access module, but only error messages in the rest of the application.</span></span> <span data-ttu-id="b89c6-112">V takovém případě byste použili přepínače jeden trasování pro modulu přístupu k datům a jeden pro zbývající aplikace.</span><span class="sxs-lookup"><span data-stu-id="b89c6-112">In that case, you would use one trace switch for the data access module and one switch for the rest of the application.</span></span> <span data-ttu-id="b89c6-113">Pomocí souboru .config nakonfigurovat přepínače na příslušná nastavení může řídit, jaké typy zpráva trasování, která se vám zobrazila.</span><span class="sxs-lookup"><span data-stu-id="b89c6-113">By using the .config file to configure the switches to the appropriate settings, you could control what types of trace message you received.</span></span> <span data-ttu-id="b89c6-114">Další informace najdete v tématu [postupy: vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).</span><span class="sxs-lookup"><span data-stu-id="b89c6-114">For more information, see [How to: Create, Initialize and Configure Trace Switches](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).</span></span>  
  
 <span data-ttu-id="b89c6-115">Obvykle je nasazené aplikace provést s jeho přepínače zakázaná, tak, aby uživatelé nemusí sledovat mnoho důležité trasování zpráv zobrazovaných na obrazovce nebo naplňování soubor protokolu jako spouštět aplikace.</span><span class="sxs-lookup"><span data-stu-id="b89c6-115">Typically, a deployed application is executed with its switches disabled, so that users need not observe a lot of irrelevant trace messages appearing on a screen or filling up a log file as the application runs.</span></span> <span data-ttu-id="b89c6-116">Pokud k problému dojde během provádění aplikací, zastavte aplikaci a povolit přepínačů restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="b89c6-116">If a problem arises during application execution, you can stop the application, enable the switches, and restart the application.</span></span> <span data-ttu-id="b89c6-117">Potom zobrazí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="b89c6-117">Then the tracing messages will be displayed.</span></span>  
  
 <span data-ttu-id="b89c6-118">Chcete-li použít přepínač musíte nejdřív vytvořit objekt přepínač z **BooleanSwitch** třída, **TraceSwitch** , nebo třída definované vývojáře přepínače.</span><span class="sxs-lookup"><span data-stu-id="b89c6-118">To use a switch you must first create a switch object from a **BooleanSwitch** class, a **TraceSwitch** class, or a developer-defined switch class.</span></span> <span data-ttu-id="b89c6-119">Další informace o vytváření definované vývojáře přepínačů najdete v tématu <xref:System.Diagnostics.Switch> třídy v odkazu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b89c6-119">For more information about creating developer-defined switches, see the <xref:System.Diagnostics.Switch> class in the .NET Framework reference.</span></span> <span data-ttu-id="b89c6-120">Pak můžete nastavit hodnotu konfigurace, která určuje, když je objekt v přepínač, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="b89c6-120">Then you set a configuration value that specifies when the switch object is to be used.</span></span> <span data-ttu-id="b89c6-121">Potom otestovat nastavení přepínače objektu v různých **trasování** (nebo **ladění**) metody trasování.</span><span class="sxs-lookup"><span data-stu-id="b89c6-121">You then test the setting of the switch object in various **Trace** (or **Debug**) tracing methods.</span></span>  
  
## <a name="trace-levels"></a><span data-ttu-id="b89c6-122">Úrovně trasování</span><span class="sxs-lookup"><span data-stu-id="b89c6-122">Trace Levels</span></span>  
 <span data-ttu-id="b89c6-123">Při použití **TraceSwitch**, existují další aspekty.</span><span class="sxs-lookup"><span data-stu-id="b89c6-123">When you use **TraceSwitch**, there are additional considerations.</span></span> <span data-ttu-id="b89c6-124">A **TraceSwitch** objekt má čtyři vlastnosti, které vracejí **Boolean** hodnoty, která určuje, jestli je přepínač nastaven alespoň na konkrétní úroveň:</span><span class="sxs-lookup"><span data-stu-id="b89c6-124">A **TraceSwitch** object has four properties that return **Boolean** values indicating whether the switch is set to at least a particular level:</span></span>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="b89c6-125">Úrovně umožňují omezit množství informací o trasování, abyste ji pouze tyto informace, které jsou potřebné k vyřešení problému.</span><span class="sxs-lookup"><span data-stu-id="b89c6-125">Levels allow you to limit the amount of tracing information you receive to only that information needed to solve a problem.</span></span> <span data-ttu-id="b89c6-126">Můžete zadat úroveň podrobností, které chcete ve výstupu trasování nastavení a konfigurace přepínačů trasování na úroveň odpovídající trasování.</span><span class="sxs-lookup"><span data-stu-id="b89c6-126">You specify the level of detail you want in your tracing output by setting and configuring trace switches to the appropriate trace level.</span></span> <span data-ttu-id="b89c6-127">Chybové zprávy, zprávy upozornění, informační zprávy, podrobného trasování zprávy nebo žádná zpráva může vůbec přijímat.</span><span class="sxs-lookup"><span data-stu-id="b89c6-127">You can receive error messages, warning messages, informational messages, verbose tracing messages, or no message at all.</span></span>  
  
 <span data-ttu-id="b89c6-128">Je zcela na vás se rozhodnout, jaký druh zpráva pro přidružení k každou úroveň.</span><span class="sxs-lookup"><span data-stu-id="b89c6-128">It is entirely up to you to decide what kind of message to associate with each level.</span></span> <span data-ttu-id="b89c6-129">Obvykle obsah trasování zprávy závisí na přidružit jednotlivé úrovně, ale určit rozdíly mezi úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="b89c6-129">Typically, the content of tracing messages depends on what you associate with each level, but you determine the differences between levels.</span></span> <span data-ttu-id="b89c6-130">Můžete chtít Zadejte podrobný popis problému na úrovni 3 (**informace**), například, ale pouze referenční číslo chyby na úrovni 1 (**chyba**).</span><span class="sxs-lookup"><span data-stu-id="b89c6-130">You might want to provide detailed descriptions of a problem at level 3 (**Info**), for example, but provide only an error reference number at level 1 (**Error**).</span></span> <span data-ttu-id="b89c6-131">Je zcela na vás nechá rozhodnout, jaké schéma funguje nejlépe ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b89c6-131">It is entirely up to you to decide what scheme works best in your application.</span></span>  
  
 <span data-ttu-id="b89c6-132">Tyto vlastnosti odpovídají hodnot 1 až 4 **TraceLevel** výčtu.</span><span class="sxs-lookup"><span data-stu-id="b89c6-132">These properties correspond to the values 1 through 4 of the **TraceLevel** enumeration.</span></span> <span data-ttu-id="b89c6-133">Následující tabulka uvádí seznam úrovní **TraceLevel** výčet a jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b89c6-133">The following table lists the levels of the **TraceLevel** enumeration and their values.</span></span>  
  
|<span data-ttu-id="b89c6-134">Výčtová hodnota</span><span class="sxs-lookup"><span data-stu-id="b89c6-134">Enumerated value</span></span>|<span data-ttu-id="b89c6-135">Celočíselná hodnota</span><span class="sxs-lookup"><span data-stu-id="b89c6-135">Integer value</span></span>|<span data-ttu-id="b89c6-136">Typ zprávy zobrazit (nebo zapisovat do zadané výstupní cíl)</span><span class="sxs-lookup"><span data-stu-id="b89c6-136">Type of message displayed (or written to a specified output target)</span></span>|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|<span data-ttu-id="b89c6-137">Off</span><span class="sxs-lookup"><span data-stu-id="b89c6-137">Off</span></span>|<span data-ttu-id="b89c6-138">0</span><span class="sxs-lookup"><span data-stu-id="b89c6-138">0</span></span>|<span data-ttu-id="b89c6-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="b89c6-139">None</span></span>|  
|<span data-ttu-id="b89c6-140">Chyba</span><span class="sxs-lookup"><span data-stu-id="b89c6-140">Error</span></span>|<span data-ttu-id="b89c6-141">1</span><span class="sxs-lookup"><span data-stu-id="b89c6-141">1</span></span>|<span data-ttu-id="b89c6-142">Pouze chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="b89c6-142">Only error messages</span></span>|  
|<span data-ttu-id="b89c6-143">Upozornění</span><span class="sxs-lookup"><span data-stu-id="b89c6-143">Warning</span></span>|<span data-ttu-id="b89c6-144">2</span><span class="sxs-lookup"><span data-stu-id="b89c6-144">2</span></span>|<span data-ttu-id="b89c6-145">Zprávy upozornění a chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="b89c6-145">Warning messages and error messages</span></span>|  
|<span data-ttu-id="b89c6-146">Informace o</span><span class="sxs-lookup"><span data-stu-id="b89c6-146">Info</span></span>|<span data-ttu-id="b89c6-147">3</span><span class="sxs-lookup"><span data-stu-id="b89c6-147">3</span></span>|<span data-ttu-id="b89c6-148">Informační zprávy, upozornění a chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="b89c6-148">Informational messages, warning messages, and error messages</span></span>|  
|<span data-ttu-id="b89c6-149">Verbose</span><span class="sxs-lookup"><span data-stu-id="b89c6-149">Verbose</span></span>|<span data-ttu-id="b89c6-150">4</span><span class="sxs-lookup"><span data-stu-id="b89c6-150">4</span></span>|<span data-ttu-id="b89c6-151">Podrobné zprávy, informační zprávy, upozornění a chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="b89c6-151">Verbose messages, informational messages, warning messages, and error messages</span></span>|  
  
 <span data-ttu-id="b89c6-152">**TraceSwitch** vlastnosti určují úroveň maximální trasování pro přepínač.</span><span class="sxs-lookup"><span data-stu-id="b89c6-152">The **TraceSwitch** properties indicate the maximum trace level for the switch.</span></span> <span data-ttu-id="b89c6-153">To znamená informace o trasování je napsán pro úroveň zadán stejně jako u všech nižších úrovních.</span><span class="sxs-lookup"><span data-stu-id="b89c6-153">That is, tracing information is written for the level specified as well as for all lower levels.</span></span> <span data-ttu-id="b89c6-154">Například pokud **TraceInfo** je **true**, pak **TraceError** a **trasování** jsou také **true** ale **TraceVerbose** dobře může být **false**.</span><span class="sxs-lookup"><span data-stu-id="b89c6-154">For example, if **TraceInfo** is **true**, then **TraceError** and **TraceWarning** are also **true** but **TraceVerbose** might well be **false**.</span></span>  
  
 <span data-ttu-id="b89c6-155">Tyto vlastnosti jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b89c6-155">These properties are read-only.</span></span> <span data-ttu-id="b89c6-156">**TraceSwitch** objekt automaticky nastaví při **TraceLevel** je nastavena.</span><span class="sxs-lookup"><span data-stu-id="b89c6-156">The **TraceSwitch** object automatically sets them when the **TraceLevel** property is set.</span></span> <span data-ttu-id="b89c6-157">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b89c6-157">For example:</span></span>  
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =   
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to   
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a><span data-ttu-id="b89c6-158">Definované vývojáře přepínače</span><span class="sxs-lookup"><span data-stu-id="b89c6-158">Developer-Defined Switches</span></span>  
 <span data-ttu-id="b89c6-159">Kromě **BooleanSwitch** a **TraceSwitch**, můžete definovat vlastní přepínače dědění ze **přepínač** třídy a přepsáním metody třídy base s vlastní metody.</span><span class="sxs-lookup"><span data-stu-id="b89c6-159">In addition to providing **BooleanSwitch** and **TraceSwitch**, you can define your own switches by inheriting from the **Switch** class and overriding the base class methods with customized methods.</span></span> <span data-ttu-id="b89c6-160">Další informace o vytváření definované vývojáře přepínačů najdete v tématu <xref:System.Diagnostics.Switch> třídy v odkazu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b89c6-160">For more information about creating developer-defined switches, see the <xref:System.Diagnostics.Switch> class in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89c6-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="b89c6-161">See Also</span></span>  
 [<span data-ttu-id="b89c6-162">Trasování – moduly naslouchání</span><span class="sxs-lookup"><span data-stu-id="b89c6-162">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="b89c6-163">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="b89c6-163">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="b89c6-164">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="b89c6-164">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
