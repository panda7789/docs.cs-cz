---
title: 'Postupy: Čtení metadat obrázku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: e2b56175e625281a920c390e5feb4238e3cb7f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182522"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="3ffad-102">Postupy: Čtení metadat obrázku</span><span class="sxs-lookup"><span data-stu-id="3ffad-102">How to: Read Image Metadata</span></span>

<span data-ttu-id="3ffad-103">Některé obrazové soubory obsahují metadata, která můžete číst, abyste určili vlastnosti obrazu.</span><span class="sxs-lookup"><span data-stu-id="3ffad-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="3ffad-104">Digitální fotografie může například obsahovat metadata, která můžete číst, abyste určili způsob a model fotoaparátu použitého k zachycení obrazu.</span><span class="sxs-lookup"><span data-stu-id="3ffad-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="3ffad-105">Pomocí gdi+ můžete číst existující metadata a můžete také zapisovat nová metadata do obrazových souborů.</span><span class="sxs-lookup"><span data-stu-id="3ffad-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>

<span data-ttu-id="3ffad-106">GDI+ ukládá jednotlivé části metadat <xref:System.Drawing.Imaging.PropertyItem> v objektu.</span><span class="sxs-lookup"><span data-stu-id="3ffad-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="3ffad-107">Můžete číst <xref:System.Drawing.Image.PropertyItems%2A> vlastnost objektu <xref:System.Drawing.Image> načíst všechna metadata ze souboru.</span><span class="sxs-lookup"><span data-stu-id="3ffad-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="3ffad-108">Vlastnost <xref:System.Drawing.Image.PropertyItems%2A> vrátí pole <xref:System.Drawing.Imaging.PropertyItem> objektů.</span><span class="sxs-lookup"><span data-stu-id="3ffad-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>

<span data-ttu-id="3ffad-109">Objekt <xref:System.Drawing.Imaging.PropertyItem> má následující čtyři `Id`vlastnosti: , `Value`, `Len`a `Type`.</span><span class="sxs-lookup"><span data-stu-id="3ffad-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>

## <a name="id"></a><span data-ttu-id="3ffad-110">ID</span><span class="sxs-lookup"><span data-stu-id="3ffad-110">Id</span></span>

<span data-ttu-id="3ffad-111">Značka, která identifikuje položku metadat.</span><span class="sxs-lookup"><span data-stu-id="3ffad-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="3ffad-112">Některé hodnoty, ke <xref:System.Drawing.Imaging.PropertyItem.Id%2A> kterým lze přiřadit, jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="3ffad-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table:</span></span>

|<span data-ttu-id="3ffad-113">Šestnáctková hodnota</span><span class="sxs-lookup"><span data-stu-id="3ffad-113">Hexadecimal value</span></span>|<span data-ttu-id="3ffad-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3ffad-114">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="3ffad-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="3ffad-115">0x0320</span></span><br /><br /> <span data-ttu-id="3ffad-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="3ffad-116">0x010F</span></span><br /><br /> <span data-ttu-id="3ffad-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="3ffad-117">0x0110</span></span><br /><br /> <span data-ttu-id="3ffad-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="3ffad-118">0x9003</span></span><br /><br /> <span data-ttu-id="3ffad-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="3ffad-119">0x829A</span></span><br /><br /> <span data-ttu-id="3ffad-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="3ffad-120">0x5090</span></span><br /><br /> <span data-ttu-id="3ffad-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="3ffad-121">0x5091</span></span>|<span data-ttu-id="3ffad-122">Název obrázku</span><span class="sxs-lookup"><span data-stu-id="3ffad-122">Image title</span></span><br /><br /> <span data-ttu-id="3ffad-123">Výrobce zařízení</span><span class="sxs-lookup"><span data-stu-id="3ffad-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="3ffad-124">Model vybavení</span><span class="sxs-lookup"><span data-stu-id="3ffad-124">Equipment model</span></span><br /><br /> <span data-ttu-id="3ffad-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="3ffad-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="3ffad-126">Exif doba expozice</span><span class="sxs-lookup"><span data-stu-id="3ffad-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="3ffad-127">Stůl jasu</span><span class="sxs-lookup"><span data-stu-id="3ffad-127">Luminance table</span></span><br /><br /> <span data-ttu-id="3ffad-128">Tabulka chrominance</span><span class="sxs-lookup"><span data-stu-id="3ffad-128">Chrominance table</span></span>|

## <a name="value"></a><span data-ttu-id="3ffad-129">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3ffad-129">Value</span></span>

<span data-ttu-id="3ffad-130">Pole hodnot.</span><span class="sxs-lookup"><span data-stu-id="3ffad-130">An array of values.</span></span> <span data-ttu-id="3ffad-131">Formát hodnot je určen vlastností. <xref:System.Drawing.Imaging.PropertyItem.Type%2A></span><span class="sxs-lookup"><span data-stu-id="3ffad-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>

## <a name="len"></a><span data-ttu-id="3ffad-132">Len</span><span class="sxs-lookup"><span data-stu-id="3ffad-132">Len</span></span>

<span data-ttu-id="3ffad-133">Délka (v bajtů) pole hodnot, na <xref:System.Drawing.Imaging.PropertyItem.Value%2A> které poukazuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3ffad-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>

## <a name="type"></a><span data-ttu-id="3ffad-134">Typ</span><span class="sxs-lookup"><span data-stu-id="3ffad-134">Type</span></span>

<span data-ttu-id="3ffad-135">Datový typ hodnot v poli, na `Value` které je vlastnost í, je datový.</span><span class="sxs-lookup"><span data-stu-id="3ffad-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="3ffad-136">Formáty označené hodnotami `Type` vlastností jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="3ffad-136">The formats indicated by the `Type` property values are shown in the following table:</span></span>

|<span data-ttu-id="3ffad-137">Číselná hodnota</span><span class="sxs-lookup"><span data-stu-id="3ffad-137">Numeric value</span></span>|<span data-ttu-id="3ffad-138">Popis</span><span class="sxs-lookup"><span data-stu-id="3ffad-138">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="3ffad-139">1</span><span class="sxs-lookup"><span data-stu-id="3ffad-139">1</span></span>|<span data-ttu-id="3ffad-140">Položka `Byte`.</span><span class="sxs-lookup"><span data-stu-id="3ffad-140">A `Byte`</span></span>|
|<span data-ttu-id="3ffad-141">2</span><span class="sxs-lookup"><span data-stu-id="3ffad-141">2</span></span>|<span data-ttu-id="3ffad-142">Pole `Byte` objektů kódovaných jako ASCII</span><span class="sxs-lookup"><span data-stu-id="3ffad-142">An array of `Byte` objects encoded as ASCII</span></span>|
|<span data-ttu-id="3ffad-143">3</span><span class="sxs-lookup"><span data-stu-id="3ffad-143">3</span></span>|<span data-ttu-id="3ffad-144">Šestnáctibitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3ffad-144">A 16-bit integer</span></span>|
|<span data-ttu-id="3ffad-145">4</span><span class="sxs-lookup"><span data-stu-id="3ffad-145">4</span></span>|<span data-ttu-id="3ffad-146">32bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3ffad-146">A 32-bit integer</span></span>|
|<span data-ttu-id="3ffad-147">5</span><span class="sxs-lookup"><span data-stu-id="3ffad-147">5</span></span>|<span data-ttu-id="3ffad-148">Pole dvou `Byte` objektů, které představují racionální číslo</span><span class="sxs-lookup"><span data-stu-id="3ffad-148">An array of two `Byte` objects that represent a rational number</span></span>|
|<span data-ttu-id="3ffad-149">6</span><span class="sxs-lookup"><span data-stu-id="3ffad-149">6</span></span>|<span data-ttu-id="3ffad-150">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="3ffad-150">Not used</span></span>|
|<span data-ttu-id="3ffad-151">7</span><span class="sxs-lookup"><span data-stu-id="3ffad-151">7</span></span>|<span data-ttu-id="3ffad-152">Nedefinované</span><span class="sxs-lookup"><span data-stu-id="3ffad-152">Undefined</span></span>|
|<span data-ttu-id="3ffad-153">8</span><span class="sxs-lookup"><span data-stu-id="3ffad-153">8</span></span>|<span data-ttu-id="3ffad-154">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="3ffad-154">Not used</span></span>|
|<span data-ttu-id="3ffad-155">9</span><span class="sxs-lookup"><span data-stu-id="3ffad-155">9</span></span>|`SLong`|
|<span data-ttu-id="3ffad-156">10</span><span class="sxs-lookup"><span data-stu-id="3ffad-156">10</span></span>|`SRational`|

## <a name="example"></a><span data-ttu-id="3ffad-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ffad-157">Example</span></span>
  
<span data-ttu-id="3ffad-158">Následující příklad kódu přečte a zobrazí sedm kusů `FakePhoto.jpg`metadat v souboru .</span><span class="sxs-lookup"><span data-stu-id="3ffad-158">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="3ffad-159">Druhá položka vlastnosti (index 1) <xref:System.Drawing.Imaging.PropertyItem.Id%2A> v seznamu má 0x010F (výrobce zařízení) a <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (bajtové pole kódované ASCII).</span><span class="sxs-lookup"><span data-stu-id="3ffad-159">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="3ffad-160">Příklad kódu zobrazuje hodnotu této položky vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3ffad-160">The code example displays the value of that property item.</span></span>

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

<span data-ttu-id="3ffad-161">Kód vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="3ffad-161">The code produces output similar to the following:</span></span>

```output
 Property Item 0
  
 id: 0x320
  
 type: 2

 length: 16 bytes
  
 Property Item 1
  
 id: 0x10f
  
 type: 2
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```

## <a name="compiling-the-code"></a><span data-ttu-id="3ffad-162">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3ffad-162">Compiling the Code</span></span>

<span data-ttu-id="3ffad-163">Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e`forms a vyžaduje <xref:System.Windows.Forms.Control.Paint> , což je parametr obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3ffad-163">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="3ffad-164">Zpracovat <xref:System.Windows.Forms.Control.Paint> událost formuláře a vložit tento kód do obslužné rutiny události malování.</span><span class="sxs-lookup"><span data-stu-id="3ffad-164">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="3ffad-165">Je nutné `FakePhoto.jpg` nahradit název obrázku a cestu platnou v systému a importovat obor `System.Drawing.Imaging` názvů.</span><span class="sxs-lookup"><span data-stu-id="3ffad-165">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ffad-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ffad-166">See also</span></span>

- [<span data-ttu-id="3ffad-167">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="3ffad-167">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="3ffad-168">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="3ffad-168">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
