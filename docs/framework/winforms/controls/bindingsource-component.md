---
title: BindingSource – komponenta
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 54639edb512a8bc6c5909282d5e4c210439e2a6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683415"
---
# <a name="bindingsource-component"></a><span data-ttu-id="e37d6-102">BindingSource – komponenta</span><span class="sxs-lookup"><span data-stu-id="e37d6-102">BindingSource Component</span></span>
<span data-ttu-id="e37d6-103">Zapouzdřuje zdroj dat pro vytvoření vazby na ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e37d6-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="e37d6-104"><xref:System.Windows.Forms.BindingSource> Komponenta má dva účely.</span><span class="sxs-lookup"><span data-stu-id="e37d6-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="e37d6-105">Nejprve poskytuje úroveň dereference při vytvoření vazby ovládacích prvků ve formuláři na data.</span><span class="sxs-lookup"><span data-stu-id="e37d6-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="e37d6-106">To lze provést pomocí vytvoření vazby <xref:System.Windows.Forms.BindingSource> zdroje dat a následným vytvoření vazby ovládacích prvků na formuláři pro komponentu <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="e37d6-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="e37d6-107">Všechny další interakce s daty, včetně navigace, řazení, filtrování a aktualizace, se provádí pomocí volání <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="e37d6-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="e37d6-108">Druhý, <xref:System.Windows.Forms.BindingSource> komponenta může fungovat jako zdroj dat silného typu.</span><span class="sxs-lookup"><span data-stu-id="e37d6-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="e37d6-109">Přidání typu <xref:System.Windows.Forms.BindingSource> komponentu s <xref:System.Windows.Forms.BindingSource.Add%2A> metoda vytvoří seznam daného typu.</span><span class="sxs-lookup"><span data-stu-id="e37d6-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e37d6-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e37d6-110">In This Section</span></span>  
 [<span data-ttu-id="e37d6-111">Přehled komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="e37d6-111">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)  
 <span data-ttu-id="e37d6-112">Představuje obecné koncepty <xref:System.Windows.Forms.BindingSource> součásti, která umožňuje vytvoření vazby zdroje dat k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="e37d6-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="e37d6-113">Postupy: Vytvoření vazby ovládacích prvků Windows Forms k hodnotám databáze DBNull</span><span class="sxs-lookup"><span data-stu-id="e37d6-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="e37d6-114">Ukazuje, jak zpracovat <xref:System.DBNull> hodnoty ze zdroje dat s použitím <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="e37d6-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="e37d6-115">Postupy: Řazení a filtrování dat ADO.NET pomocí Windows Forms BindingSource – komponenta</span><span class="sxs-lookup"><span data-stu-id="e37d6-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="e37d6-116">Ukazuje použití <xref:System.Windows.Forms.BindingSource> seřadí součást, kterou použít a filtruje data zobrazená.</span><span class="sxs-lookup"><span data-stu-id="e37d6-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="e37d6-117">Postupy: Připojení k webové službě pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="e37d6-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="e37d6-118">Ukazuje způsob použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby k webové službě.</span><span class="sxs-lookup"><span data-stu-id="e37d6-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="e37d6-119">Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="e37d6-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="e37d6-120">Ukazuje použití <xref:System.Windows.Forms.BindingSource> komponenty pro pohodlné zpracování chyb, ke kterým dochází v datové vazbě operace.</span><span class="sxs-lookup"><span data-stu-id="e37d6-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="e37d6-121">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="e37d6-121">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="e37d6-122">Ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby k typu.</span><span class="sxs-lookup"><span data-stu-id="e37d6-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="e37d6-123">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k objektu Factory</span><span class="sxs-lookup"><span data-stu-id="e37d6-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="e37d6-124">Ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby na objekt pro vytváření objektu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="e37d6-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="e37d6-125">Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="e37d6-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="e37d6-126">Ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření nové položky a přidat je do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e37d6-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="e37d6-127">Postupy: Vytváření oznámení o změnách pomocí metody BindingSource Resetitem</span><span class="sxs-lookup"><span data-stu-id="e37d6-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="e37d6-128">Ukazuje použití <xref:System.Windows.Forms.BindingSource> součást, kterou vyvolávají události oznamování změn pro oznámení o změně zdroje dat, které nepodporují.</span><span class="sxs-lookup"><span data-stu-id="e37d6-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="e37d6-129">Postupy: Vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e37d6-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="e37d6-130">Ukazuje, jak použít typ, který dědí z <xref:System.ComponentModel.INotifyPropertyChanged> s <xref:System.Windows.Forms.BindingSource> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e37d6-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="e37d6-131">Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource</span><span class="sxs-lookup"><span data-stu-id="e37d6-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="e37d6-132">Ukazuje, jak reagovat na změny ve zdroji dat pomocí <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="e37d6-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="e37d6-133">Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="e37d6-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="e37d6-134">Ukazuje způsob použití <xref:System.Windows.Forms.BindingSource> svázat více formulářů do stejného datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="e37d6-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e37d6-135">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e37d6-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="e37d6-136">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="e37d6-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="e37d6-137">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e37d6-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e37d6-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e37d6-138">Related Sections</span></span>  
 [<span data-ttu-id="e37d6-139">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="e37d6-139">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="e37d6-140">Obsahuje odkazy na témata popisující architektura vazby dat formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="e37d6-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="e37d6-141">Viz také [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e37d6-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
