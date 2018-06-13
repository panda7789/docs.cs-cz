---
title: 'Postupy: Vytvoření datového objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
ms.openlocfilehash: d10b9ce70ce98e5fcbf8b08e4f22cea4c22d1df0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544778"
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="9f4d7-102">Postupy: Vytvoření datového objektu</span><span class="sxs-lookup"><span data-stu-id="9f4d7-102">How to: Create a Data Object</span></span>
<span data-ttu-id="9f4d7-103">Následující příklady ukazují různé způsoby, jak vytvořit objekt dat pomocí konstruktorů poskytované <xref:System.Windows.DataObject> třídy.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f4d7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f4d7-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9f4d7-105">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4d7-105">Description</span></span>  
 <span data-ttu-id="9f4d7-106">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) k inicializaci objektu data řetězcem.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="9f4d7-107">V takovém případě formátu příslušná data je určena automaticky podle typu uložených dat a automaticky převádění uložených dat je povoleno ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f4d7-108">Kód</span><span class="sxs-lookup"><span data-stu-id="9f4d7-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="9f4d7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4d7-109">Description</span></span>  
 <span data-ttu-id="9f4d7-110">Následující příklad kódu je zhuštěný verzi výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f4d7-111">Kód</span><span class="sxs-lookup"><span data-stu-id="9f4d7-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="9f4d7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f4d7-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9f4d7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4d7-113">Description</span></span>  
 <span data-ttu-id="9f4d7-114">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) k inicializaci objektu data s řetězec a formátu zadaná data.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="9f4d7-115">V takovém případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typ řetězce.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="9f4d7-116">Automatický převod uložených dat je ve výchozím nastavení povolena.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f4d7-117">Kód</span><span class="sxs-lookup"><span data-stu-id="9f4d7-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="9f4d7-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4d7-118">Description</span></span>  
 <span data-ttu-id="9f4d7-119">Následující příklad kódu je zhuštěný verzi výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f4d7-120">Kód</span><span class="sxs-lookup"><span data-stu-id="9f4d7-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="9f4d7-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f4d7-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9f4d7-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4d7-122">Description</span></span>  
 <span data-ttu-id="9f4d7-123">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory (<xref:System.Windows.DataObject.%23ctor%2A>) k inicializaci objektu data s řetězec a formátu zadaná data.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="9f4d7-124">V takovém případě je zadána formát dat <xref:System.Type> parametr.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="9f4d7-125">Automatický převod uložených dat je ve výchozím nastavení povolena.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f4d7-126">Kód</span><span class="sxs-lookup"><span data-stu-id="9f4d7-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="9f4d7-127">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4d7-127">Description</span></span>  
 <span data-ttu-id="9f4d7-128">Následující příklad kódu je zhuštěný verzi výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f4d7-129">Kód</span><span class="sxs-lookup"><span data-stu-id="9f4d7-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="9f4d7-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f4d7-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9f4d7-131">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4d7-131">Description</span></span>  
 <span data-ttu-id="9f4d7-132">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) k inicializaci objektu data s řetězec a formátu zadaná data.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="9f4d7-133">V takovém případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typ řetězce.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="9f4d7-134">Toto přetížení konkrétní konstruktor umožňuje volajícímu zadat, zda je povolen převedení automaticky.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f4d7-135">Kód</span><span class="sxs-lookup"><span data-stu-id="9f4d7-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="9f4d7-136">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4d7-136">Description</span></span>  
 <span data-ttu-id="9f4d7-137">Následující příklad kódu je zhuštěný verzi výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="9f4d7-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f4d7-138">Kód</span><span class="sxs-lookup"><span data-stu-id="9f4d7-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="9f4d7-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f4d7-139">See Also</span></span>  
 <xref:System.Windows.IDataObject>
