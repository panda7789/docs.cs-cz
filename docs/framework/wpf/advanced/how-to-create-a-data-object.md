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
ms.openlocfilehash: deae8751518d9322e8d924a1b1fcbc20e25b35ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121784"
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="65666-102">Postupy: Vytvoření datového objektu</span><span class="sxs-lookup"><span data-stu-id="65666-102">How to: Create a Data Object</span></span>
<span data-ttu-id="65666-103">Následující příklady znázorňují různé způsoby vytvoření datového objektu pomocí konstruktorů poskytované <xref:System.Windows.DataObject> třídy.</span><span class="sxs-lookup"><span data-stu-id="65666-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65666-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="65666-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="65666-105">Popis</span><span class="sxs-lookup"><span data-stu-id="65666-105">Description</span></span>  
 <span data-ttu-id="65666-106">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) k inicializaci dat objektu s řetězcem.</span><span class="sxs-lookup"><span data-stu-id="65666-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="65666-107">V tomto případě má formát příslušná data je určena automaticky podle typu uložených dat a automatického převodu objem uložených dat je ve výchozím nastavení povolený.</span><span class="sxs-lookup"><span data-stu-id="65666-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65666-108">Kód</span><span class="sxs-lookup"><span data-stu-id="65666-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="65666-109">Popis</span><span class="sxs-lookup"><span data-stu-id="65666-109">Description</span></span>  
 <span data-ttu-id="65666-110">Následující příklad kódu je zkrácenou verzi kódu, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="65666-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65666-111">Kód</span><span class="sxs-lookup"><span data-stu-id="65666-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="65666-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="65666-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="65666-113">Popis</span><span class="sxs-lookup"><span data-stu-id="65666-113">Description</span></span>  
 <span data-ttu-id="65666-114">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) k inicializaci dat objektu řetězce a zadaného data formátu.</span><span class="sxs-lookup"><span data-stu-id="65666-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="65666-115">V tomto případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typů řetězců.</span><span class="sxs-lookup"><span data-stu-id="65666-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="65666-116">Automatický převod uložených dat je ve výchozím nastavení povolený.</span><span class="sxs-lookup"><span data-stu-id="65666-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65666-117">Kód</span><span class="sxs-lookup"><span data-stu-id="65666-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="65666-118">Popis</span><span class="sxs-lookup"><span data-stu-id="65666-118">Description</span></span>  
 <span data-ttu-id="65666-119">Následující příklad kódu je zkrácenou verzi kódu, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="65666-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65666-120">Kód</span><span class="sxs-lookup"><span data-stu-id="65666-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="65666-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="65666-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="65666-122">Popis</span><span class="sxs-lookup"><span data-stu-id="65666-122">Description</span></span>  
 <span data-ttu-id="65666-123">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů (<xref:System.Windows.DataObject.%23ctor%2A>) k inicializaci dat objektu řetězce a zadaného data formátu.</span><span class="sxs-lookup"><span data-stu-id="65666-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="65666-124">V tomto případě je určený formát data <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="65666-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="65666-125">Automatický převod uložených dat je ve výchozím nastavení povolený.</span><span class="sxs-lookup"><span data-stu-id="65666-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65666-126">Kód</span><span class="sxs-lookup"><span data-stu-id="65666-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="65666-127">Popis</span><span class="sxs-lookup"><span data-stu-id="65666-127">Description</span></span>  
 <span data-ttu-id="65666-128">Následující příklad kódu je zkrácenou verzi kódu, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="65666-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65666-129">Kód</span><span class="sxs-lookup"><span data-stu-id="65666-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="65666-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="65666-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="65666-131">Popis</span><span class="sxs-lookup"><span data-stu-id="65666-131">Description</span></span>  
 <span data-ttu-id="65666-132">Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) k inicializaci dat objektu řetězce a zadaného data formátu.</span><span class="sxs-lookup"><span data-stu-id="65666-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="65666-133">V tomto případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typů řetězců.</span><span class="sxs-lookup"><span data-stu-id="65666-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="65666-134">Tohoto konkrétního konstruktoru přetížení umožňuje volajícímu zadat, zda je povolen automatický převod.</span><span class="sxs-lookup"><span data-stu-id="65666-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65666-135">Kód</span><span class="sxs-lookup"><span data-stu-id="65666-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="65666-136">Popis</span><span class="sxs-lookup"><span data-stu-id="65666-136">Description</span></span>  
 <span data-ttu-id="65666-137">Následující příklad kódu je zkrácenou verzi kódu, uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="65666-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65666-138">Kód</span><span class="sxs-lookup"><span data-stu-id="65666-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="65666-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65666-139">See also</span></span>

- <xref:System.Windows.IDataObject>
