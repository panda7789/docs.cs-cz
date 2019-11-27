---
title: My.Forms – objekt
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: db86704fdc8120ccac5f4489c80a515834ad888f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350363"
---
# <a name="myforms-object"></a><span data-ttu-id="3c15b-102">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="3c15b-102">My.Forms Object</span></span>

<span data-ttu-id="3c15b-103">Poskytuje vlastnosti pro přístup k instanci každého formuláře Windows deklarovaného v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="3c15b-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c15b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c15b-104">Remarks</span></span>

<span data-ttu-id="3c15b-105">Objekt `My.Forms` poskytuje instanci každého formuláře v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="3c15b-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="3c15b-106">Název vlastnosti je stejný jako název formuláře, ke kterému vlastnost přistupuje.</span><span class="sxs-lookup"><span data-stu-id="3c15b-106">The name of the property is the same as the name of the form that the property accesses.</span></span>

<span data-ttu-id="3c15b-107">K formulářům poskytovaným objektem `My.Forms` můžete přistupovat pomocí názvu formuláře bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="3c15b-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="3c15b-108">Vzhledem k tomu, že název vlastnosti je stejný jako název typu formuláře, umožňuje přístup k formuláři, jako by měl výchozí instanci.</span><span class="sxs-lookup"><span data-stu-id="3c15b-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="3c15b-109">Například `My.Forms.Form1.Show` je ekvivalentem `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="3c15b-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>

<span data-ttu-id="3c15b-110">Objekt `My.Forms` zpřístupňuje pouze formuláře přidružené k aktuálnímu projektu.</span><span class="sxs-lookup"><span data-stu-id="3c15b-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="3c15b-111">Neposkytuje přístup k formulářům deklarovaným v odkazovaných knihovnách DLL.</span><span class="sxs-lookup"><span data-stu-id="3c15b-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="3c15b-112">Chcete-li získat přístup k formuláři, který poskytuje knihovna DLL, je nutné použít kvalifikovaný název formuláře, který je napsán jako *Název_souboru_DLL*. *Formace*.</span><span class="sxs-lookup"><span data-stu-id="3c15b-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>

<span data-ttu-id="3c15b-113">Vlastnost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> lze použít k získání kolekce všech otevřených formulářů aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c15b-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>

<span data-ttu-id="3c15b-114">Objekt a jeho vlastnosti jsou k dispozici pouze pro aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3c15b-114">The object and its properties are available only for Windows applications.</span></span>

## <a name="properties"></a><span data-ttu-id="3c15b-115">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3c15b-115">Properties</span></span>

<span data-ttu-id="3c15b-116">Každá vlastnost objektu `My.Forms` poskytuje přístup k instanci formuláře v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="3c15b-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="3c15b-117">Název vlastnosti je stejný jako název formuláře, ke kterému vlastnost přistupuje, a typ vlastnosti je stejný jako typ formuláře.</span><span class="sxs-lookup"><span data-stu-id="3c15b-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>

> [!NOTE]
> <span data-ttu-id="3c15b-118">Pokud dojde ke kolizi názvů, název vlastnosti pro přístup k formuláři je *RootNamespace*_*názvový prostor*\_název *formuláře*.</span><span class="sxs-lookup"><span data-stu-id="3c15b-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="3c15b-119">Například zvažte dva formuláře s názvem `Form1.`, pokud je jeden z těchto formulářů v kořenovém oboru názvů `WindowsApplication1` a v `Namespace1`oboru názvů, měli byste k tomuto formuláři přistupovat prostřednictvím `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="3c15b-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>

<span data-ttu-id="3c15b-120">Objekt `My.Forms` poskytuje přístup k instanci hlavního formuláře aplikace, který byl vytvořen při spuštění.</span><span class="sxs-lookup"><span data-stu-id="3c15b-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="3c15b-121">Pro všechny ostatní formuláře vytvoří objekt `My.Forms` novou instanci formuláře, když je k němu přidaný a uložený.</span><span class="sxs-lookup"><span data-stu-id="3c15b-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="3c15b-122">Následné pokusy o přístup k této vlastnosti vrátí tuto instanci formuláře.</span><span class="sxs-lookup"><span data-stu-id="3c15b-122">Subsequent attempts to access that property return that instance of the form.</span></span>

<span data-ttu-id="3c15b-123">Formulář můžete vyřadit přiřazením `Nothing` k vlastnosti tohoto formuláře.</span><span class="sxs-lookup"><span data-stu-id="3c15b-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="3c15b-124">Vlastnost setter volá metodu <xref:System.Windows.Forms.Form.Close%2A> formuláře a potom přiřadí `Nothing` uložené hodnotě.</span><span class="sxs-lookup"><span data-stu-id="3c15b-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="3c15b-125">Pokud k vlastnosti přiřadíte jinou hodnotu než `Nothing`, vyvolá metoda setter výjimku <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="3c15b-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="3c15b-126">Můžete otestovat, zda vlastnost objektu `My.Forms` ukládá instanci formuláře pomocí operátoru `Is` nebo `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="3c15b-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="3c15b-127">Tyto operátory můžete použít ke kontrole, zda je hodnota vlastnosti `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3c15b-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>

> [!NOTE]
> <span data-ttu-id="3c15b-128">Operátor `Is` nebo `IsNot` obvykle musí číst hodnotu vlastnosti pro provedení porovnání.</span><span class="sxs-lookup"><span data-stu-id="3c15b-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="3c15b-129">Pokud však vlastnost aktuálně ukládá `Nothing`, vlastnost vytvoří novou instanci formuláře a následně vrátí tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="3c15b-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="3c15b-130">Nicméně kompilátor Visual Basic pracuje s vlastnostmi objektu `My.Forms` odlišně a umožňuje operátoru `Is` nebo `IsNot` ke kontrole stavu vlastnosti bez změny její hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3c15b-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>

## <a name="example"></a><span data-ttu-id="3c15b-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c15b-131">Example</span></span>

<span data-ttu-id="3c15b-132">Tento příklad změní název výchozího formuláře `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="3c15b-132">This example changes the title of the default `SidebarMenu` form.</span></span>

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

<span data-ttu-id="3c15b-133">Aby tento příklad fungoval, projekt musí mít formulář s názvem `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="3c15b-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>

<span data-ttu-id="3c15b-134">Tento kód bude fungovat pouze v projektu aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3c15b-134">This code will work only in a Windows Application project.</span></span>

## <a name="requirements"></a><span data-ttu-id="3c15b-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c15b-135">Requirements</span></span>

### <a name="availability-by-project-type"></a><span data-ttu-id="3c15b-136">Dostupnost podle typu projektu</span><span class="sxs-lookup"><span data-stu-id="3c15b-136">Availability by Project Type</span></span>

|<span data-ttu-id="3c15b-137">Typ projektu</span><span class="sxs-lookup"><span data-stu-id="3c15b-137">Project type</span></span>|<span data-ttu-id="3c15b-138">K dispozici</span><span class="sxs-lookup"><span data-stu-id="3c15b-138">Available</span></span>|
|---|---|
|<span data-ttu-id="3c15b-139">Aplikace systému Windows</span><span class="sxs-lookup"><span data-stu-id="3c15b-139">Windows Application</span></span>|<span data-ttu-id="3c15b-140">**Ano**</span><span class="sxs-lookup"><span data-stu-id="3c15b-140">**Yes**</span></span>|
|<span data-ttu-id="3c15b-141">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="3c15b-141">Class Library</span></span>|<span data-ttu-id="3c15b-142">Ne</span><span class="sxs-lookup"><span data-stu-id="3c15b-142">No</span></span>|
|<span data-ttu-id="3c15b-143">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="3c15b-143">Console Application</span></span>|<span data-ttu-id="3c15b-144">Ne</span><span class="sxs-lookup"><span data-stu-id="3c15b-144">No</span></span>|
|<span data-ttu-id="3c15b-145">Knihovna ovládacích prvků Windows</span><span class="sxs-lookup"><span data-stu-id="3c15b-145">Windows Control Library</span></span>|<span data-ttu-id="3c15b-146">Ne</span><span class="sxs-lookup"><span data-stu-id="3c15b-146">No</span></span>|
|<span data-ttu-id="3c15b-147">Knihovna webového ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3c15b-147">Web Control Library</span></span>|<span data-ttu-id="3c15b-148">Ne</span><span class="sxs-lookup"><span data-stu-id="3c15b-148">No</span></span>|
|<span data-ttu-id="3c15b-149">Služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="3c15b-149">Windows Service</span></span>|<span data-ttu-id="3c15b-150">Ne</span><span class="sxs-lookup"><span data-stu-id="3c15b-150">No</span></span>|
|<span data-ttu-id="3c15b-151">Web</span><span class="sxs-lookup"><span data-stu-id="3c15b-151">Web Site</span></span>|<span data-ttu-id="3c15b-152">Ne</span><span class="sxs-lookup"><span data-stu-id="3c15b-152">No</span></span>|

## <a name="see-also"></a><span data-ttu-id="3c15b-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c15b-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="3c15b-154">Objekty</span><span class="sxs-lookup"><span data-stu-id="3c15b-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)
- [<span data-ttu-id="3c15b-155">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="3c15b-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="3c15b-156">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="3c15b-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="3c15b-157">Přístup k formulářům aplikace</span><span class="sxs-lookup"><span data-stu-id="3c15b-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
