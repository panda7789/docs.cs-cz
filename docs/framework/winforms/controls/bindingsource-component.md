---
title: "BindingSource – komponenta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08b55bc2bd5af78eb6c3d0f5adce3ec39d288a9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="bindingsource-component"></a><span data-ttu-id="34ebf-102">BindingSource – komponenta</span><span class="sxs-lookup"><span data-stu-id="34ebf-102">BindingSource Component</span></span>
<span data-ttu-id="34ebf-103">Zapouzdří zdroj dat pro vytvoření vazby na ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="34ebf-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="34ebf-104"><xref:System.Windows.Forms.BindingSource> Součást má dva účely.</span><span class="sxs-lookup"><span data-stu-id="34ebf-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="34ebf-105">Nejprve poskytuje úroveň dereference při vytvoření vazby ovládacích prvků na formuláři na data.</span><span class="sxs-lookup"><span data-stu-id="34ebf-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="34ebf-106">Toho dosahuje pomocí vytvoření vazby <xref:System.Windows.Forms.BindingSource> součásti pro zdroj dat a následným vytvoření vazby ovládacích prvků na formuláři na <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="34ebf-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="34ebf-107">Všechny další interakce s daty, včetně navigace, řazení, filtrování a aktualizace, se provádí pomocí volání <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="34ebf-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="34ebf-108">Druhý, <xref:System.Windows.Forms.BindingSource> součást může fungovat jako zdroj dat silného typu.</span><span class="sxs-lookup"><span data-stu-id="34ebf-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="34ebf-109">Přidání typu k <xref:System.Windows.Forms.BindingSource> součásti s <xref:System.Windows.Forms.BindingSource.Add%2A> metoda vytvoří seznam daného typu.</span><span class="sxs-lookup"><span data-stu-id="34ebf-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34ebf-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="34ebf-110">In This Section</span></span>  
 [<span data-ttu-id="34ebf-111">Přehled komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="34ebf-111">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 <span data-ttu-id="34ebf-112">Představuje obecné koncepty <xref:System.Windows.Forms.BindingSource> komponenta, která umožňuje svázat zdroj dat k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="34ebf-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="34ebf-113">Postupy: Vytvoření vazby ovládacích prvků Windows Forms k hodnotám databáze DBNull</span><span class="sxs-lookup"><span data-stu-id="34ebf-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="34ebf-114">Ukazuje, jak zpracovat <xref:System.DBNull> hodnotu ze zdroje dat pomocí <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="34ebf-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="34ebf-115">Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="34ebf-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="34ebf-116">Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součást použít seřadí a filtrů zobrazená data.</span><span class="sxs-lookup"><span data-stu-id="34ebf-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="34ebf-117">Postupy: Vytvoření vazby k webové službě pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="34ebf-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="34ebf-118">Ukazuje, jak používat <xref:System.Windows.Forms.BindingSource> součásti pro připojení k webové službě.</span><span class="sxs-lookup"><span data-stu-id="34ebf-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="34ebf-119">Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="34ebf-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="34ebf-120">Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součásti pro pohodlné zpracování chyb vzniklých v operaci vazby na data.</span><span class="sxs-lookup"><span data-stu-id="34ebf-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="34ebf-121">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="34ebf-121">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="34ebf-122">Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součásti pro vazbu na typ.</span><span class="sxs-lookup"><span data-stu-id="34ebf-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="34ebf-123">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k objektu factory</span><span class="sxs-lookup"><span data-stu-id="34ebf-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="34ebf-124">Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součást vytvořit vazbu objekt factory nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="34ebf-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="34ebf-125">Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="34ebf-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="34ebf-126">Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součást je přidejte do zdroje dat a vytvořit nové položky.</span><span class="sxs-lookup"><span data-stu-id="34ebf-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="34ebf-127">Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="34ebf-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="34ebf-128">Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součást umožňuje aktivovat události upozornění na změnu pro oznámení o změně zdroje dat, které nepodporují.</span><span class="sxs-lookup"><span data-stu-id="34ebf-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="34ebf-129">Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="34ebf-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="34ebf-130">Ukazuje, jak používat typ, který dědí z <xref:System.ComponentModel.INotifyPropertyChanged> s <xref:System.Windows.Forms.BindingSource> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="34ebf-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="34ebf-131">Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource</span><span class="sxs-lookup"><span data-stu-id="34ebf-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="34ebf-132">Ukazuje, jak reagovat na změny v zdroje dat pomocí <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="34ebf-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="34ebf-133">Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="34ebf-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="34ebf-134">Ukazuje, jak používat <xref:System.Windows.Forms.BindingSource> k vytvoření vazby formuláře více stejný zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="34ebf-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="34ebf-135">Odkaz</span><span class="sxs-lookup"><span data-stu-id="34ebf-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="34ebf-136">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="34ebf-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="34ebf-137">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="34ebf-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="34ebf-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="34ebf-138">Related Sections</span></span>  
 [<span data-ttu-id="34ebf-139">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="34ebf-139">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="34ebf-140">Obsahuje odkazy na témata s popisem architektuře vazby dat Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="34ebf-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="34ebf-141">Viz také [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="34ebf-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
