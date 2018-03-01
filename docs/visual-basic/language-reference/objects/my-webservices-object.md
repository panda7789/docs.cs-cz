---
title: "My.WebServices – objekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9f2c4017a1df8059f2cc57e7c30a96c474cfda0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mywebservices-object"></a><span data-ttu-id="be3c6-102">My.WebServices – objekt</span><span class="sxs-lookup"><span data-stu-id="be3c6-102">My.WebServices Object</span></span>
<span data-ttu-id="be3c6-103">Poskytuje vlastnosti pro vytváření a přístup k jediné instance každého XML webové služby odkazuje v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="be3c6-103">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be3c6-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be3c6-104">Remarks</span></span>  
 <span data-ttu-id="be3c6-105">`My.WebServices` Objekt poskytuje instanci každé webové služby odkazuje v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="be3c6-105">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="be3c6-106">Každá instance je vytvořena na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="be3c6-106">Each instance is instantiated on demand.</span></span> <span data-ttu-id="be3c6-107">Tyto webové služby můžete přistupovat prostřednictvím vlastnosti `My.WebServices` objektu.</span><span class="sxs-lookup"><span data-stu-id="be3c6-107">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="be3c6-108">Název vlastnosti je stejný jako název webové služby, který má přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="be3c6-108">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="be3c6-109">Všechny třídy, která dědí z <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> je webová služba.</span><span class="sxs-lookup"><span data-stu-id="be3c6-109">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="be3c6-110">Informace o přidání do projektu webové služby najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="be3c6-110">For information about adding Web services to a project, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="be3c6-111">`My.WebServices` Objekt se poskytuje pouze webové služby přidružené k aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="be3c6-111">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="be3c6-112">Neposkytuje přístup k webovým službám, které jsou deklarované v odkazované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="be3c6-112">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="be3c6-113">Pro přístup k webové službě, která poskytuje knihovnu DLL, musíte použít kvalifikovaný název webové služby, ve tvaru *názevsouboru*. *WebServiceName*.</span><span class="sxs-lookup"><span data-stu-id="be3c6-113">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="be3c6-114">Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="be3c6-114">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="be3c6-115">Objekt a jeho vlastnosti nejsou k dispozici pro webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="be3c6-115">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="be3c6-116">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="be3c6-116">Properties</span></span>  
 <span data-ttu-id="be3c6-117">Každou vlastnost `My.WebServices` objekt poskytuje přístup k instanci webové služby odkazuje v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="be3c6-117">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="be3c6-118">Název vlastnosti je stejný jako název webové služby, který má přístup k vlastnosti a typ vlastnosti je stejný jako typ webovou službu.</span><span class="sxs-lookup"><span data-stu-id="be3c6-118">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be3c6-119">Pokud je kolize názvů, je název vlastnosti pro přístup k webové službě *RootNamespace*_*Namespace*\_*ServiceName*.</span><span class="sxs-lookup"><span data-stu-id="be3c6-119">If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="be3c6-120">Představte si třeba dva webové služby s názvem `Service1`.</span><span class="sxs-lookup"><span data-stu-id="be3c6-120">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="be3c6-121">Pokud jeden z těchto služeb je v kořenovém oboru názvů `WindowsApplication1` a v oboru názvů `Namespace1`, bude přístup k této službě pomocí `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span><span class="sxs-lookup"><span data-stu-id="be3c6-121">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="be3c6-122">Pokud nejprve přístup mezi `My.WebServices` vlastností objektu vytvoří novou instanci třídy webové služby a uloží ji.</span><span class="sxs-lookup"><span data-stu-id="be3c6-122">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="be3c6-123">Následných přístupech této vlastnosti vrátí tuto instanci webové služby.</span><span class="sxs-lookup"><span data-stu-id="be3c6-123">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="be3c6-124">Můžete vyřazení webové služby přiřazením `Nothing` vlastnosti pro tuto webovou službu.</span><span class="sxs-lookup"><span data-stu-id="be3c6-124">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="be3c6-125">Metoda setter vlastnosti přiřadí `Nothing` uložené hodnotě.</span><span class="sxs-lookup"><span data-stu-id="be3c6-125">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="be3c6-126">Chcete-li přiřadit žádnou hodnotu než `Nothing` pro vlastnost, nastavovací metoda vyvolá <xref:System.ArgumentException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="be3c6-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="be3c6-127">Můžete zkontrolovat, zda vlastnost `My.WebServices` objekt ukládá instance webové služby pomocí `Is` nebo `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="be3c6-127">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="be3c6-128">Tyto operátory můžete zkontrolovat, zda je hodnota vlastnosti `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="be3c6-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be3c6-129">Obvykle `Is` nebo `IsNot` operátor má načíst hodnotu vlastnosti, která má-li provést porovnání.</span><span class="sxs-lookup"><span data-stu-id="be3c6-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="be3c6-130">Ale pokud vlastnost aktuálně ukládá `Nothing`, vlastnost vytvoří novou instanci webové služby a vrátí tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="be3c6-130">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="be3c6-131">Ale Visual Basic – kompilátor zpracovává vlastnosti `My.WebServices` speciálně objektu a umožňuje `Is` nebo `IsNot` operátor a zkontrolujte stav vlastnosti beze změny jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="be3c6-131">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be3c6-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="be3c6-132">Example</span></span>  
 <span data-ttu-id="be3c6-133">Tento příklad volá `FahrenheitToCelsius` metodu `TemperatureConverter` XML webové služby a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="be3c6-133">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 <span data-ttu-id="be3c6-134">Pro tento příklad fungoval, musí odkazovat projektu webové služby s názvem `Converter`, a že webové služby musí vystavit `ConvertTemperature` metoda.</span><span class="sxs-lookup"><span data-stu-id="be3c6-134">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="be3c6-135">Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="be3c6-135">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="be3c6-136">Tento kód nefunguje v projektu webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="be3c6-136">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be3c6-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be3c6-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="be3c6-138">Dostupnost podle typu projektu</span><span class="sxs-lookup"><span data-stu-id="be3c6-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="be3c6-139">Typ projektu</span><span class="sxs-lookup"><span data-stu-id="be3c6-139">Project type</span></span>|<span data-ttu-id="be3c6-140">K dispozici</span><span class="sxs-lookup"><span data-stu-id="be3c6-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="be3c6-141">Aplikace systému Windows</span><span class="sxs-lookup"><span data-stu-id="be3c6-141">Windows Application</span></span>|<span data-ttu-id="be3c6-142">**Ano**</span><span class="sxs-lookup"><span data-stu-id="be3c6-142">**Yes**</span></span>|  
|<span data-ttu-id="be3c6-143">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="be3c6-143">Class Library</span></span>|<span data-ttu-id="be3c6-144">**Ano**</span><span class="sxs-lookup"><span data-stu-id="be3c6-144">**Yes**</span></span>|  
|<span data-ttu-id="be3c6-145">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="be3c6-145">Console Application</span></span>|<span data-ttu-id="be3c6-146">**Ano**</span><span class="sxs-lookup"><span data-stu-id="be3c6-146">**Yes**</span></span>|  
|<span data-ttu-id="be3c6-147">Knihovna ovládacích prvků Windows</span><span class="sxs-lookup"><span data-stu-id="be3c6-147">Windows Control Library</span></span>|<span data-ttu-id="be3c6-148">**Ano**</span><span class="sxs-lookup"><span data-stu-id="be3c6-148">**Yes**</span></span>|  
|<span data-ttu-id="be3c6-149">Knihovna webových prvků</span><span class="sxs-lookup"><span data-stu-id="be3c6-149">Web Control Library</span></span>|<span data-ttu-id="be3c6-150">**Ano**</span><span class="sxs-lookup"><span data-stu-id="be3c6-150">**Yes**</span></span>|  
|<span data-ttu-id="be3c6-151">Služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="be3c6-151">Windows Service</span></span>|<span data-ttu-id="be3c6-152">**Ano**</span><span class="sxs-lookup"><span data-stu-id="be3c6-152">**Yes**</span></span>|  
|<span data-ttu-id="be3c6-153">Webový server</span><span class="sxs-lookup"><span data-stu-id="be3c6-153">Web Site</span></span>|<span data-ttu-id="be3c6-154">Ne</span><span class="sxs-lookup"><span data-stu-id="be3c6-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be3c6-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="be3c6-155">See Also</span></span>  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="be3c6-156">Přístup k aplikačním webovým službám</span><span class="sxs-lookup"><span data-stu-id="be3c6-156">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
