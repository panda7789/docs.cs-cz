---
title: My.Forms – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: d15765b7673f321d4362ceea0adb73959a7e7726
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784998"
---
# <a name="myforms-object"></a><span data-ttu-id="6ddb2-102">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="6ddb2-102">My.Forms Object</span></span>
<span data-ttu-id="6ddb2-103">Poskytuje vlastnosti pro přístup k instanci jednotlivých formulářů Windows deklarované v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ddb2-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ddb2-104">Remarks</span></span>  
 <span data-ttu-id="6ddb2-105">`My.Forms` Objekt, který poskytuje instance každý formulář v nástrojích pro aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="6ddb2-106">Název vlastnosti je stejný jako název formuláře, který přistupuje k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="6ddb2-107">Dostanete formuláře nabízené modulem `My.Forms` s použitím jméno ve tvaru, bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="6ddb2-108">Název vlastnosti je stejný jako název typu formuláře, to umožňuje přístup do formuláře, jako kdyby byla výchozí instanci.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="6ddb2-109">Například `My.Forms.Form1.Show` je ekvivalentní `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="6ddb2-110">`My.Forms` Zpřístupňuje pouze formuláře, které jsou přidružené k aktuálnímu projektu.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="6ddb2-111">Neposkytuje přístup k formulářům deklarované v odkazované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="6ddb2-112">Pro přístup k formuláře, který obsahuje knihovnu DLL, musíte použít kvalifikovaný název v podobě, zapsán jako *názevsouboru*. *FormName*.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="6ddb2-113">Můžete použít <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> vlastnost získat kolekci formulářů otevřít všechny aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="6ddb2-114">Objekt a její vlastnosti jsou k dispozici pouze pro aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6ddb2-115">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6ddb2-115">Properties</span></span>  
 <span data-ttu-id="6ddb2-116">Každou vlastnost `My.Forms` objekt, který poskytuje přístup k instanci formulář v nástrojích pro aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="6ddb2-117">Název vlastnosti je stejný jako název formuláře, který přistupuje k vlastnosti, a typ vlastnosti je stejný jako typ formuláře.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ddb2-118">Pokud je kolize názvů, název vlastnosti pro přístup k formuláři je *RootNamespace*_*Namespace*\_*FormName*.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="6ddb2-119">Představte si třeba dvě formy s názvem `Form1.`-li jednu z těchto forem, je v kořenovém oboru názvů `WindowsApplication1` a v oboru názvů `Namespace1`, můžete k, které tvoří prostřednictvím `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="6ddb2-120">`My.Forms` Objekt, který poskytuje přístup k instanci aplikace hlavního formuláře, který byl vytvořen při spuštění.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="6ddb2-121">Pro všechny ostatní způsoby `My.Forms` objekt vytvoří novou instanci formuláře, když přistupuje a uloží jej.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="6ddb2-122">Následné pokusy o přístup k této vlastnosti vrácení této instance formuláře.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="6ddb2-123">Můžete uvolnit formuláře přiřazením `Nothing` na vlastnost pro daný formulář.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="6ddb2-124">Volání metody setter vlastnosti <xref:System.Windows.Forms.Form.Close%2A> metoda formulář, a poté přiřadí `Nothing` k uložené hodnotě.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="6ddb2-125">Pokud přiřadíte libovolnou hodnotu jiné než `Nothing` na vlastnost, vyvolá metoda setter <xref:System.ArgumentException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="6ddb2-126">Můžete zkontrolovat, jestli vlastnost `My.Forms` ukládá instance formulář pomocí `Is` nebo `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="6ddb2-127">Chcete-li zkontrolovat, zda je hodnota vlastnosti můžete použít tyto operátory `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ddb2-128">Obvykle `Is` nebo `IsNot` operátor má být přečtena hodnota vlastnosti k provádění porovnání.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="6ddb2-129">Nicméně pokud aktuálně uchovává vlastnost `Nothing`, vlastnost vytvoří novou instanci formuláře a vrátí tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="6ddb2-130">Však kompilátor jazyka Visual Basic zpracovává vlastnosti `My.Forms` jinak objektu a umožňuje `Is` nebo `IsNot` operátor zkontrolovat stav vlastnost beze změny jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ddb2-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ddb2-131">Example</span></span>  
 <span data-ttu-id="6ddb2-132">V tomto příkladu změní název výchozí `SidebarMenu` formuláře.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="6ddb2-133">Pro tento příklad fungoval, musí mít váš projekt formulář s názvem `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="6ddb2-134">Tento kód bude fungovat pouze v projektu aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="6ddb2-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ddb2-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ddb2-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="6ddb2-136">Dostupnost podle typu projektu</span><span class="sxs-lookup"><span data-stu-id="6ddb2-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="6ddb2-137">Typ projektu</span><span class="sxs-lookup"><span data-stu-id="6ddb2-137">Project type</span></span>|<span data-ttu-id="6ddb2-138">K dispozici</span><span class="sxs-lookup"><span data-stu-id="6ddb2-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="6ddb2-139">Aplikace Windows</span><span class="sxs-lookup"><span data-stu-id="6ddb2-139">Windows Application</span></span>|<span data-ttu-id="6ddb2-140">**Ano**</span><span class="sxs-lookup"><span data-stu-id="6ddb2-140">**Yes**</span></span>|  
|<span data-ttu-id="6ddb2-141">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="6ddb2-141">Class Library</span></span>|<span data-ttu-id="6ddb2-142">Ne</span><span class="sxs-lookup"><span data-stu-id="6ddb2-142">No</span></span>|  
|<span data-ttu-id="6ddb2-143">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="6ddb2-143">Console Application</span></span>|<span data-ttu-id="6ddb2-144">Ne</span><span class="sxs-lookup"><span data-stu-id="6ddb2-144">No</span></span>|  
|<span data-ttu-id="6ddb2-145">Knihovna ovládacích prvků Windows</span><span class="sxs-lookup"><span data-stu-id="6ddb2-145">Windows Control Library</span></span>|<span data-ttu-id="6ddb2-146">Ne</span><span class="sxs-lookup"><span data-stu-id="6ddb2-146">No</span></span>|  
|<span data-ttu-id="6ddb2-147">Knihovna webových prvků</span><span class="sxs-lookup"><span data-stu-id="6ddb2-147">Web Control Library</span></span>|<span data-ttu-id="6ddb2-148">Ne</span><span class="sxs-lookup"><span data-stu-id="6ddb2-148">No</span></span>|  
|<span data-ttu-id="6ddb2-149">Služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="6ddb2-149">Windows Service</span></span>|<span data-ttu-id="6ddb2-150">Ne</span><span class="sxs-lookup"><span data-stu-id="6ddb2-150">No</span></span>|  
|<span data-ttu-id="6ddb2-151">Webové stránky</span><span class="sxs-lookup"><span data-stu-id="6ddb2-151">Web Site</span></span>|<span data-ttu-id="6ddb2-152">Ne</span><span class="sxs-lookup"><span data-stu-id="6ddb2-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ddb2-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ddb2-153">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="6ddb2-154">Objekty</span><span class="sxs-lookup"><span data-stu-id="6ddb2-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="6ddb2-155">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="6ddb2-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="6ddb2-156">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="6ddb2-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="6ddb2-157">Přístup k formulářům aplikace</span><span class="sxs-lookup"><span data-stu-id="6ddb2-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
