---
title: "Postupy: Vytvoření datového objektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7b002e1c7a9eea2592de58aac3b838b9f6f982ce
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="36740-102">Postupy: Vytvoření datového objektu</span><span class="sxs-lookup"><span data-stu-id="36740-102">How to: Create a Data Object</span></span>
<span data-ttu-id="36740-103">Následující příklady ukazují různé způsoby, jak vytvořit objekt dat pomocí konstruktorů poskytované <xref:System.Windows.DataObject> třídy.</span><span class="sxs-lookup"><span data-stu-id="36740-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36740-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="36740-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="36740-105">Popis</span><span class="sxs-lookup"><span data-stu-id="36740-105">Description</span></span>  
 <span data-ttu-id="36740-106">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) k inicializaci objektu data řetězcem.</span><span class="sxs-lookup"><span data-stu-id="36740-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="36740-107">V takovém případě formátu příslušná data je určena automaticky podle typu uložených dat a automaticky převádění uložených dat je povoleno ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="36740-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36740-108">Kód</span><span class="sxs-lookup"><span data-stu-id="36740-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="36740-109">Popis</span><span class="sxs-lookup"><span data-stu-id="36740-109">Description</span></span>  
 <span data-ttu-id="36740-110">Následující příklad kódu je zhuštěný verzi výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="36740-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36740-111">Kód</span><span class="sxs-lookup"><span data-stu-id="36740-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="36740-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="36740-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="36740-113">Popis</span><span class="sxs-lookup"><span data-stu-id="36740-113">Description</span></span>  
 <span data-ttu-id="36740-114">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) k inicializaci objektu data s řetězec a formátu zadaná data.</span><span class="sxs-lookup"><span data-stu-id="36740-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="36740-115">V takovém případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typ řetězce.</span><span class="sxs-lookup"><span data-stu-id="36740-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="36740-116">Automatický převod uložených dat je ve výchozím nastavení povolena.</span><span class="sxs-lookup"><span data-stu-id="36740-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36740-117">Kód</span><span class="sxs-lookup"><span data-stu-id="36740-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="36740-118">Popis</span><span class="sxs-lookup"><span data-stu-id="36740-118">Description</span></span>  
 <span data-ttu-id="36740-119">Následující příklad kódu je zhuštěný verzi výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="36740-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36740-120">Kód</span><span class="sxs-lookup"><span data-stu-id="36740-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="36740-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="36740-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="36740-122">Popis</span><span class="sxs-lookup"><span data-stu-id="36740-122">Description</span></span>  
 <span data-ttu-id="36740-123">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory (<xref:System.Windows.DataObject.%23ctor%2A>) k inicializaci objektu data s řetězec a formátu zadaná data.</span><span class="sxs-lookup"><span data-stu-id="36740-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="36740-124">V takovém případě je zadána formát dat <xref:System.Type> parametr.</span><span class="sxs-lookup"><span data-stu-id="36740-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="36740-125">Automatický převod uložených dat je ve výchozím nastavení povolena.</span><span class="sxs-lookup"><span data-stu-id="36740-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36740-126">Kód</span><span class="sxs-lookup"><span data-stu-id="36740-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="36740-127">Popis</span><span class="sxs-lookup"><span data-stu-id="36740-127">Description</span></span>  
 <span data-ttu-id="36740-128">Následující příklad kódu je zhuštěný verzi výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="36740-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36740-129">Kód</span><span class="sxs-lookup"><span data-stu-id="36740-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="36740-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="36740-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="36740-131">Popis</span><span class="sxs-lookup"><span data-stu-id="36740-131">Description</span></span>  
 <span data-ttu-id="36740-132">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) k inicializaci objektu data s řetězec a formátu zadaná data.</span><span class="sxs-lookup"><span data-stu-id="36740-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="36740-133">V takovém případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typ řetězce.</span><span class="sxs-lookup"><span data-stu-id="36740-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="36740-134">Toto přetížení konkrétní konstruktor umožňuje volajícímu zadat, zda je povolen převedení automaticky.</span><span class="sxs-lookup"><span data-stu-id="36740-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36740-135">Kód</span><span class="sxs-lookup"><span data-stu-id="36740-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="36740-136">Popis</span><span class="sxs-lookup"><span data-stu-id="36740-136">Description</span></span>  
 <span data-ttu-id="36740-137">Následující příklad kódu je zhuštěný verzi výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="36740-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36740-138">Kód</span><span class="sxs-lookup"><span data-stu-id="36740-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="36740-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="36740-139">See Also</span></span>  
 <xref:System.Windows.IDataObject>
