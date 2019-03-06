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
ms.openlocfilehash: f7bdfbf3dba0c700513348195c1d031d4c2c8b65
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370589"
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="48b3d-102">Postupy: Vytvoření datového objektu</span><span class="sxs-lookup"><span data-stu-id="48b3d-102">How to: Create a Data Object</span></span>
<span data-ttu-id="48b3d-103">Následující příklady znázorňují různé způsoby vytvoření datového objektu pomocí konstruktorů poskytované <xref:System.Windows.DataObject> třídy.</span><span class="sxs-lookup"><span data-stu-id="48b3d-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48b3d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="48b3d-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="48b3d-105">Popis</span><span class="sxs-lookup"><span data-stu-id="48b3d-105">Description</span></span>  
 <span data-ttu-id="48b3d-106">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) k inicializaci dat objektu s řetězcem.</span><span class="sxs-lookup"><span data-stu-id="48b3d-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="48b3d-107">V tomto případě má formát příslušná data je určena automaticky podle typu uložených dat a automatického převodu objem uložených dat je ve výchozím nastavení povolený.</span><span class="sxs-lookup"><span data-stu-id="48b3d-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48b3d-108">Kód</span><span class="sxs-lookup"><span data-stu-id="48b3d-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="48b3d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="48b3d-109">Description</span></span>  
 <span data-ttu-id="48b3d-110">Následující příklad kódu je zkrácenou verzi kódu, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="48b3d-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48b3d-111">Kód</span><span class="sxs-lookup"><span data-stu-id="48b3d-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="48b3d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="48b3d-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="48b3d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="48b3d-113">Description</span></span>  
 <span data-ttu-id="48b3d-114">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) k inicializaci dat objektu řetězce a zadaného data formátu.</span><span class="sxs-lookup"><span data-stu-id="48b3d-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="48b3d-115">V tomto případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typů řetězců.</span><span class="sxs-lookup"><span data-stu-id="48b3d-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="48b3d-116">Automatický převod uložených dat je ve výchozím nastavení povolený.</span><span class="sxs-lookup"><span data-stu-id="48b3d-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48b3d-117">Kód</span><span class="sxs-lookup"><span data-stu-id="48b3d-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="48b3d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="48b3d-118">Description</span></span>  
 <span data-ttu-id="48b3d-119">Následující příklad kódu je zkrácenou verzi kódu, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="48b3d-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48b3d-120">Kód</span><span class="sxs-lookup"><span data-stu-id="48b3d-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="48b3d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="48b3d-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="48b3d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="48b3d-122">Description</span></span>  
 <span data-ttu-id="48b3d-123">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů (<xref:System.Windows.DataObject.%23ctor%2A>) k inicializaci dat objektu řetězce a zadaného data formátu.</span><span class="sxs-lookup"><span data-stu-id="48b3d-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="48b3d-124">V tomto případě je určený formát data <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="48b3d-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="48b3d-125">Automatický převod uložených dat je ve výchozím nastavení povolený.</span><span class="sxs-lookup"><span data-stu-id="48b3d-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48b3d-126">Kód</span><span class="sxs-lookup"><span data-stu-id="48b3d-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="48b3d-127">Popis</span><span class="sxs-lookup"><span data-stu-id="48b3d-127">Description</span></span>  
 <span data-ttu-id="48b3d-128">Následující příklad kódu je zkrácenou verzi kódu, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="48b3d-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48b3d-129">Kód</span><span class="sxs-lookup"><span data-stu-id="48b3d-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="48b3d-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="48b3d-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="48b3d-131">Popis</span><span class="sxs-lookup"><span data-stu-id="48b3d-131">Description</span></span>  
 <span data-ttu-id="48b3d-132">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) k inicializaci dat objektu řetězce a zadaného data formátu.</span><span class="sxs-lookup"><span data-stu-id="48b3d-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="48b3d-133">V tomto případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typů řetězců.</span><span class="sxs-lookup"><span data-stu-id="48b3d-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="48b3d-134">Tohoto konkrétního konstruktoru přetížení umožňuje volajícímu zadat, zda je povolen automatický převod.</span><span class="sxs-lookup"><span data-stu-id="48b3d-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48b3d-135">Kód</span><span class="sxs-lookup"><span data-stu-id="48b3d-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="48b3d-136">Popis</span><span class="sxs-lookup"><span data-stu-id="48b3d-136">Description</span></span>  
 <span data-ttu-id="48b3d-137">Následující příklad kódu je zkrácenou verzi kódu, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="48b3d-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48b3d-138">Kód</span><span class="sxs-lookup"><span data-stu-id="48b3d-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="48b3d-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48b3d-139">See also</span></span>
- <xref:System.Windows.IDataObject>
