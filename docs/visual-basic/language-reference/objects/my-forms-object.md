---
title: "My.Forms – objekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a><span data-ttu-id="f67bb-102">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="f67bb-102">My.Forms Object</span></span>
<span data-ttu-id="f67bb-103">Poskytuje vlastnosti pro přístup k instanci jednotlivých formulářů Windows, které jsou deklarované v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f67bb-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f67bb-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f67bb-104">Remarks</span></span>  
 <span data-ttu-id="f67bb-105">`My.Forms` Objekt poskytuje instanci každého formuláře v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f67bb-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="f67bb-106">Název vlastnosti je stejný jako název ve tvaru, který přistupuje k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f67bb-106">The name of the property is the same as the name of the form that the property accesses.</span></span> <span data-ttu-id="f67bb-107">Informace o přidávání formuláře do projektu najdete v tématu [postupy: Přidání Windows Forms do projektu](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="f67bb-107">For information about adding forms to a project, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="f67bb-108">Dostanete formulářích, které `My.Forms` objektu pomocí názvu formuláře, bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="f67bb-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="f67bb-109">Název vlastnosti je stejný jako název typu formuláře, to umožňuje přístup do formuláře jako, pokud má výchozí instance.</span><span class="sxs-lookup"><span data-stu-id="f67bb-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="f67bb-110">Například `My.Forms.Form1.Show` je ekvivalentní `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="f67bb-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="f67bb-111">`My.Forms` Objekt se poskytuje pouze formuláře, které jsou přidružené k aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="f67bb-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="f67bb-112">Neposkytuje přístup k formulářům deklarované v odkazované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="f67bb-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="f67bb-113">Pro přístup k formuláři, který knihovny DLL, musíte použít kvalifikovaný název ve tvaru, zapisují jako *názevsouboru*. *Položky název formuláře*.</span><span class="sxs-lookup"><span data-stu-id="f67bb-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="f67bb-114">Můžete použít <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> vlastnost k získání kolekce otevřených formulářů všechny aplikace.</span><span class="sxs-lookup"><span data-stu-id="f67bb-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="f67bb-115">Objekt a jeho vlastnosti jsou k dispozici pouze pro aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f67bb-115">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f67bb-116">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f67bb-116">Properties</span></span>  
 <span data-ttu-id="f67bb-117">Každou vlastnost `My.Forms` objekt poskytuje přístup k instanci formuláře v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f67bb-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="f67bb-118">Název vlastnosti je stejný jako název ve tvaru, který přistupuje k vlastnosti a typ vlastnosti je stejný jako typ formuláře.</span><span class="sxs-lookup"><span data-stu-id="f67bb-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f67bb-119">Pokud je kolize názvů, název vlastnosti pro přístup k formuláři je *RootNamespace*_*Namespace*\_*položky název formuláře*.</span><span class="sxs-lookup"><span data-stu-id="f67bb-119">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="f67bb-120">Představte si třeba dva formuláře s názvem `Form1.`Pokud jeden z těchto formulářů je v oboru názvů kořenové `WindowsApplication1` a v oboru názvů `Namespace1`, by přístup Tato forma prostřednictvím `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="f67bb-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="f67bb-121">`My.Forms` Objekt poskytuje přístup k instanci aplikace hlavní formulář, který byl vytvořen při spuštění.</span><span class="sxs-lookup"><span data-stu-id="f67bb-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="f67bb-122">Pro všechny ostatní způsoby `My.Forms` objekt vytvoří novou instanci formuláře při přístupu k a uloží ji.</span><span class="sxs-lookup"><span data-stu-id="f67bb-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="f67bb-123">Následné pokusy o přístup k vlastnosti vrátí tuto instanci formuláře.</span><span class="sxs-lookup"><span data-stu-id="f67bb-123">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="f67bb-124">Můžete vyřazení formuláře přiřazením `Nothing` pro vlastnost pro daný formulář.</span><span class="sxs-lookup"><span data-stu-id="f67bb-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="f67bb-125">Vlastnost setter volání <xref:System.Windows.Forms.Form.Close%2A> metoda formuláře, a poté přiřadí `Nothing` uložené hodnotě.</span><span class="sxs-lookup"><span data-stu-id="f67bb-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="f67bb-126">Chcete-li přiřadit žádnou hodnotu než `Nothing` pro vlastnost, nastavovací metoda vyvolá <xref:System.ArgumentException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="f67bb-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="f67bb-127">Můžete zkontrolovat, zda vlastnost `My.Forms` objekt ukládá instance formuláře pomocí `Is` nebo `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="f67bb-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="f67bb-128">Tyto operátory můžete zkontrolovat, zda je hodnota vlastnosti `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f67bb-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f67bb-129">Obvykle `Is` nebo `IsNot` operátor má načíst hodnotu vlastnosti, která má-li provést porovnání.</span><span class="sxs-lookup"><span data-stu-id="f67bb-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="f67bb-130">Ale pokud vlastnost aktuálně ukládá `Nothing`, vlastnost vytvoří novou instanci třídy formuláře a vrátí tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="f67bb-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="f67bb-131">Ale Visual Basic – kompilátor zpracovává vlastnosti `My.Forms` objektu jinak a umožňuje `Is` nebo `IsNot` operátor a zkontrolujte stav vlastnosti beze změny jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f67bb-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f67bb-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="f67bb-132">Example</span></span>  
 <span data-ttu-id="f67bb-133">Tento příklad změní název výchozí `SidebarMenu` formuláře.</span><span class="sxs-lookup"><span data-stu-id="f67bb-133">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="f67bb-134">Pro tento příklad fungoval, musí mít váš projekt formuláře s názvem `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="f67bb-134">For this example to work, your project must have a form named `SidebarMenu`.</span></span> <span data-ttu-id="f67bb-135">Další informace najdete v tématu [postupy: Přidání Windows Forms do projektu](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="f67bb-135">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="f67bb-136">Tento kód bude fungovat pouze v projektu aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f67bb-136">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f67bb-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f67bb-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="f67bb-138">Dostupnost podle typu projektu</span><span class="sxs-lookup"><span data-stu-id="f67bb-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="f67bb-139">Typ projektu</span><span class="sxs-lookup"><span data-stu-id="f67bb-139">Project type</span></span>|<span data-ttu-id="f67bb-140">K dispozici</span><span class="sxs-lookup"><span data-stu-id="f67bb-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="f67bb-141">Aplikace systému Windows</span><span class="sxs-lookup"><span data-stu-id="f67bb-141">Windows Application</span></span>|<span data-ttu-id="f67bb-142">**Ano**</span><span class="sxs-lookup"><span data-stu-id="f67bb-142">**Yes**</span></span>|  
|<span data-ttu-id="f67bb-143">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="f67bb-143">Class Library</span></span>|<span data-ttu-id="f67bb-144">Ne</span><span class="sxs-lookup"><span data-stu-id="f67bb-144">No</span></span>|  
|<span data-ttu-id="f67bb-145">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="f67bb-145">Console Application</span></span>|<span data-ttu-id="f67bb-146">Ne</span><span class="sxs-lookup"><span data-stu-id="f67bb-146">No</span></span>|  
|<span data-ttu-id="f67bb-147">Knihovna ovládacích prvků Windows</span><span class="sxs-lookup"><span data-stu-id="f67bb-147">Windows Control Library</span></span>|<span data-ttu-id="f67bb-148">Ne</span><span class="sxs-lookup"><span data-stu-id="f67bb-148">No</span></span>|  
|<span data-ttu-id="f67bb-149">Knihovna webových prvků</span><span class="sxs-lookup"><span data-stu-id="f67bb-149">Web Control Library</span></span>|<span data-ttu-id="f67bb-150">Ne</span><span class="sxs-lookup"><span data-stu-id="f67bb-150">No</span></span>|  
|<span data-ttu-id="f67bb-151">Služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="f67bb-151">Windows Service</span></span>|<span data-ttu-id="f67bb-152">Ne</span><span class="sxs-lookup"><span data-stu-id="f67bb-152">No</span></span>|  
|<span data-ttu-id="f67bb-153">Webový server</span><span class="sxs-lookup"><span data-stu-id="f67bb-153">Web Site</span></span>|<span data-ttu-id="f67bb-154">Ne</span><span class="sxs-lookup"><span data-stu-id="f67bb-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f67bb-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="f67bb-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="f67bb-156">Objekty</span><span class="sxs-lookup"><span data-stu-id="f67bb-156">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="f67bb-157">Postupy: přidání do projektu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f67bb-157">How to: Add Windows Forms to a Project</span></span>](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [<span data-ttu-id="f67bb-158">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="f67bb-158">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="f67bb-159">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="f67bb-159">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="f67bb-160">Přístup k formulářům aplikace</span><span class="sxs-lookup"><span data-stu-id="f67bb-160">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
