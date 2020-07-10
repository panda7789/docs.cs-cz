---
title: 'Postupy: Čtení metadat obrázku'
desription: Learn how to read the Windows Forms PropertyItems property of an Image object to retrieve all the metadata from a file.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 814cb17feba1e1e3a42b2bc403b0b4c828caf90e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174663"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="42f3e-102">Postupy: Čtení metadat obrázku</span><span class="sxs-lookup"><span data-stu-id="42f3e-102">How to: Read Image Metadata</span></span>

<span data-ttu-id="42f3e-103">Některé soubory obrázků obsahují metadata, která lze číst k určení funkcí obrázku.</span><span class="sxs-lookup"><span data-stu-id="42f3e-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="42f3e-104">Digitální fotografie například může obsahovat metadata, která lze číst a určit tak model a model kamery použité k zachycení bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="42f3e-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="42f3e-105">Pomocí rozhraní GDI+ si můžete přečíst existující metadata a můžete také zapisovat nová metadata do souborů obrázků.</span><span class="sxs-lookup"><span data-stu-id="42f3e-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>

<span data-ttu-id="42f3e-106">GDI+ ukládá jednotlivé části metadat do <xref:System.Drawing.Imaging.PropertyItem> objektu.</span><span class="sxs-lookup"><span data-stu-id="42f3e-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="42f3e-107">Můžete číst <xref:System.Drawing.Image.PropertyItems%2A> vlastnost <xref:System.Drawing.Image> objektu pro načtení všech metadat ze souboru.</span><span class="sxs-lookup"><span data-stu-id="42f3e-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="42f3e-108"><xref:System.Drawing.Image.PropertyItems%2A>Vlastnost vrací pole <xref:System.Drawing.Imaging.PropertyItem> objektů.</span><span class="sxs-lookup"><span data-stu-id="42f3e-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>

<span data-ttu-id="42f3e-109"><xref:System.Drawing.Imaging.PropertyItem>Objekt má následující čtyři vlastnosti: `Id` ,, a `Value` `Len` `Type` .</span><span class="sxs-lookup"><span data-stu-id="42f3e-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>

## <a name="id"></a><span data-ttu-id="42f3e-110">ID</span><span class="sxs-lookup"><span data-stu-id="42f3e-110">Id</span></span>

<span data-ttu-id="42f3e-111">Značka, která identifikuje položku metadat.</span><span class="sxs-lookup"><span data-stu-id="42f3e-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="42f3e-112">Některé hodnoty, které lze přiřadit k, <xref:System.Drawing.Imaging.PropertyItem.Id%2A> jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="42f3e-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table:</span></span>

|<span data-ttu-id="42f3e-113">Hexadecimální hodnota</span><span class="sxs-lookup"><span data-stu-id="42f3e-113">Hexadecimal value</span></span>|<span data-ttu-id="42f3e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="42f3e-114">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="42f3e-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="42f3e-115">0x0320</span></span><br /><br /> <span data-ttu-id="42f3e-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="42f3e-116">0x010F</span></span><br /><br /> <span data-ttu-id="42f3e-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="42f3e-117">0x0110</span></span><br /><br /> <span data-ttu-id="42f3e-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="42f3e-118">0x9003</span></span><br /><br /> <span data-ttu-id="42f3e-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="42f3e-119">0x829A</span></span><br /><br /> <span data-ttu-id="42f3e-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="42f3e-120">0x5090</span></span><br /><br /> <span data-ttu-id="42f3e-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="42f3e-121">0x5091</span></span>|<span data-ttu-id="42f3e-122">Název obrázku</span><span class="sxs-lookup"><span data-stu-id="42f3e-122">Image title</span></span><br /><br /> <span data-ttu-id="42f3e-123">Výrobce zařízení</span><span class="sxs-lookup"><span data-stu-id="42f3e-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="42f3e-124">Model vybavení</span><span class="sxs-lookup"><span data-stu-id="42f3e-124">Equipment model</span></span><br /><br /> <span data-ttu-id="42f3e-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="42f3e-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="42f3e-126">Doba expozice EXIF</span><span class="sxs-lookup"><span data-stu-id="42f3e-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="42f3e-127">Světlá tabulka</span><span class="sxs-lookup"><span data-stu-id="42f3e-127">Luminance table</span></span><br /><br /> <span data-ttu-id="42f3e-128">Tabulka chrominance</span><span class="sxs-lookup"><span data-stu-id="42f3e-128">Chrominance table</span></span>|

## <a name="value"></a><span data-ttu-id="42f3e-129">Hodnota</span><span class="sxs-lookup"><span data-stu-id="42f3e-129">Value</span></span>

<span data-ttu-id="42f3e-130">Pole hodnot.</span><span class="sxs-lookup"><span data-stu-id="42f3e-130">An array of values.</span></span> <span data-ttu-id="42f3e-131">Formát hodnot je určen <xref:System.Drawing.Imaging.PropertyItem.Type%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="42f3e-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>

## <a name="len"></a><span data-ttu-id="42f3e-132">Len</span><span class="sxs-lookup"><span data-stu-id="42f3e-132">Len</span></span>

<span data-ttu-id="42f3e-133">Délka (v bajtech) pole hodnot, na které se odkazuje <xref:System.Drawing.Imaging.PropertyItem.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="42f3e-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>

## <a name="type"></a><span data-ttu-id="42f3e-134">Typ</span><span class="sxs-lookup"><span data-stu-id="42f3e-134">Type</span></span>

<span data-ttu-id="42f3e-135">Datový typ hodnot v poli, na který odkazuje `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="42f3e-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="42f3e-136">Formáty, které jsou uvedeny v `Type` hodnotách vlastností, jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="42f3e-136">The formats indicated by the `Type` property values are shown in the following table:</span></span>

|<span data-ttu-id="42f3e-137">Číselná hodnota</span><span class="sxs-lookup"><span data-stu-id="42f3e-137">Numeric value</span></span>|<span data-ttu-id="42f3e-138">Popis</span><span class="sxs-lookup"><span data-stu-id="42f3e-138">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="42f3e-139">1</span><span class="sxs-lookup"><span data-stu-id="42f3e-139">1</span></span>|<span data-ttu-id="42f3e-140">Provede `Byte`.</span><span class="sxs-lookup"><span data-stu-id="42f3e-140">A `Byte`</span></span>|
|<span data-ttu-id="42f3e-141">2</span><span class="sxs-lookup"><span data-stu-id="42f3e-141">2</span></span>|<span data-ttu-id="42f3e-142">Pole `Byte` objektů kódovaných jako ASCII</span><span class="sxs-lookup"><span data-stu-id="42f3e-142">An array of `Byte` objects encoded as ASCII</span></span>|
|<span data-ttu-id="42f3e-143">3</span><span class="sxs-lookup"><span data-stu-id="42f3e-143">3</span></span>|<span data-ttu-id="42f3e-144">16bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="42f3e-144">A 16-bit integer</span></span>|
|<span data-ttu-id="42f3e-145">4</span><span class="sxs-lookup"><span data-stu-id="42f3e-145">4</span></span>|<span data-ttu-id="42f3e-146">32 celé číslo</span><span class="sxs-lookup"><span data-stu-id="42f3e-146">A 32-bit integer</span></span>|
|<span data-ttu-id="42f3e-147">5</span><span class="sxs-lookup"><span data-stu-id="42f3e-147">5</span></span>|<span data-ttu-id="42f3e-148">Pole dvou `Byte` objektů, které reprezentují racionální číslo</span><span class="sxs-lookup"><span data-stu-id="42f3e-148">An array of two `Byte` objects that represent a rational number</span></span>|
|<span data-ttu-id="42f3e-149">6</span><span class="sxs-lookup"><span data-stu-id="42f3e-149">6</span></span>|<span data-ttu-id="42f3e-150">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="42f3e-150">Not used</span></span>|
|<span data-ttu-id="42f3e-151">7</span><span class="sxs-lookup"><span data-stu-id="42f3e-151">7</span></span>|<span data-ttu-id="42f3e-152">Nedefinované</span><span class="sxs-lookup"><span data-stu-id="42f3e-152">Undefined</span></span>|
|<span data-ttu-id="42f3e-153">8</span><span class="sxs-lookup"><span data-stu-id="42f3e-153">8</span></span>|<span data-ttu-id="42f3e-154">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="42f3e-154">Not used</span></span>|
|<span data-ttu-id="42f3e-155">9</span><span class="sxs-lookup"><span data-stu-id="42f3e-155">9</span></span>|`SLong`|
|<span data-ttu-id="42f3e-156">10</span><span class="sxs-lookup"><span data-stu-id="42f3e-156">10</span></span>|`SRational`|

## <a name="example"></a><span data-ttu-id="42f3e-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="42f3e-157">Example</span></span>
  
<span data-ttu-id="42f3e-158">Následující příklad kódu načte a zobrazí sedm částí metadat v souboru `FakePhoto.jpg` .</span><span class="sxs-lookup"><span data-stu-id="42f3e-158">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="42f3e-159">Druhá položka vlastnosti (index 1) v seznamu má <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (výrobce vybavení) a <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (bajtové pole s kódováním ASCII).</span><span class="sxs-lookup"><span data-stu-id="42f3e-159">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="42f3e-160">V příkladu kódu se zobrazí hodnota této položky vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="42f3e-160">The code example displays the value of that property item.</span></span>

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

<span data-ttu-id="42f3e-161">Kód vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="42f3e-161">The code produces output similar to the following:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="42f3e-162">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="42f3e-162">Compiling the Code</span></span>

<span data-ttu-id="42f3e-163">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e` , což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="42f3e-163">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="42f3e-164">Zpracujte <xref:System.Windows.Forms.Control.Paint> událost formuláře a vložte tento kód do obslužné rutiny události Paint.</span><span class="sxs-lookup"><span data-stu-id="42f3e-164">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="42f3e-165">Je nutné nahradit `FakePhoto.jpg` názvem Image a cestou platnými v systému a importovat `System.Drawing.Imaging` obor názvů.</span><span class="sxs-lookup"><span data-stu-id="42f3e-165">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="42f3e-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="42f3e-166">See also</span></span>

- [<span data-ttu-id="42f3e-167">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="42f3e-167">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="42f3e-168">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="42f3e-168">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
