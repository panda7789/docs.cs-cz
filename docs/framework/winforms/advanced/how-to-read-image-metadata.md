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
ms.openlocfilehash: cd3b636f8f0058d4a8eacc656f95d5f46b8967e2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040751"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="a719b-102">Postupy: Čtení metadat obrázku</span><span class="sxs-lookup"><span data-stu-id="a719b-102">How to: Read Image Metadata</span></span>

<span data-ttu-id="a719b-103">Některé soubory obrázků obsahují metadata, která lze číst k určení funkcí obrázku.</span><span class="sxs-lookup"><span data-stu-id="a719b-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="a719b-104">Digitální fotografie například může obsahovat metadata, která lze číst a určit tak model a model kamery použité k zachycení bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a719b-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="a719b-105">Pomocí rozhraní GDI+ si můžete přečíst existující metadata a můžete také zapisovat nová metadata do souborů obrázků.</span><span class="sxs-lookup"><span data-stu-id="a719b-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>

<span data-ttu-id="a719b-106">GDI+ ukládá jednotlivé části metadat do objektu <xref:System.Drawing.Imaging.PropertyItem>.</span><span class="sxs-lookup"><span data-stu-id="a719b-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="a719b-107">Můžete číst vlastnost <xref:System.Drawing.Image.PropertyItems%2A> objektu <xref:System.Drawing.Image> pro načtení všech metadat ze souboru.</span><span class="sxs-lookup"><span data-stu-id="a719b-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="a719b-108">Vlastnost <xref:System.Drawing.Image.PropertyItems%2A> vrací pole objektů <xref:System.Drawing.Imaging.PropertyItem>.</span><span class="sxs-lookup"><span data-stu-id="a719b-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>

<span data-ttu-id="a719b-109">Objekt <xref:System.Drawing.Imaging.PropertyItem> má následující čtyři vlastnosti: `Id`, `Value`, `Len`a `Type`.</span><span class="sxs-lookup"><span data-stu-id="a719b-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>

## <a name="id"></a><span data-ttu-id="a719b-110">Účet</span><span class="sxs-lookup"><span data-stu-id="a719b-110">Id</span></span>

<span data-ttu-id="a719b-111">Značka, která identifikuje položku metadat.</span><span class="sxs-lookup"><span data-stu-id="a719b-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="a719b-112">Některé hodnoty, které je možné přiřadit <xref:System.Drawing.Imaging.PropertyItem.Id%2A>, jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a719b-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table:</span></span>

|<span data-ttu-id="a719b-113">Hexadecimální hodnota</span><span class="sxs-lookup"><span data-stu-id="a719b-113">Hexadecimal value</span></span>|<span data-ttu-id="a719b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a719b-114">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="a719b-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="a719b-115">0x0320</span></span><br /><br /> <span data-ttu-id="a719b-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="a719b-116">0x010F</span></span><br /><br /> <span data-ttu-id="a719b-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="a719b-117">0x0110</span></span><br /><br /> <span data-ttu-id="a719b-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="a719b-118">0x9003</span></span><br /><br /> <span data-ttu-id="a719b-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="a719b-119">0x829A</span></span><br /><br /> <span data-ttu-id="a719b-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="a719b-120">0x5090</span></span><br /><br /> <span data-ttu-id="a719b-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="a719b-121">0x5091</span></span>|<span data-ttu-id="a719b-122">Název obrázku</span><span class="sxs-lookup"><span data-stu-id="a719b-122">Image title</span></span><br /><br /> <span data-ttu-id="a719b-123">Výrobce zařízení</span><span class="sxs-lookup"><span data-stu-id="a719b-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="a719b-124">Model vybavení</span><span class="sxs-lookup"><span data-stu-id="a719b-124">Equipment model</span></span><br /><br /> <span data-ttu-id="a719b-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="a719b-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="a719b-126">Doba expozice EXIF</span><span class="sxs-lookup"><span data-stu-id="a719b-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="a719b-127">Světlá tabulka</span><span class="sxs-lookup"><span data-stu-id="a719b-127">Luminance table</span></span><br /><br /> <span data-ttu-id="a719b-128">Tabulka chrominance</span><span class="sxs-lookup"><span data-stu-id="a719b-128">Chrominance table</span></span>|

## <a name="value"></a><span data-ttu-id="a719b-129">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a719b-129">Value</span></span>

<span data-ttu-id="a719b-130">Pole hodnot.</span><span class="sxs-lookup"><span data-stu-id="a719b-130">An array of values.</span></span> <span data-ttu-id="a719b-131">Formát hodnot je určený vlastností <xref:System.Drawing.Imaging.PropertyItem.Type%2A>.</span><span class="sxs-lookup"><span data-stu-id="a719b-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>

## <a name="len"></a><span data-ttu-id="a719b-132">Funkce</span><span class="sxs-lookup"><span data-stu-id="a719b-132">Len</span></span>

<span data-ttu-id="a719b-133">Délka (v bajtech) pole hodnot, na které ukazuje vlastnost <xref:System.Drawing.Imaging.PropertyItem.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="a719b-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>

## <a name="type"></a><span data-ttu-id="a719b-134">Typ</span><span class="sxs-lookup"><span data-stu-id="a719b-134">Type</span></span>

<span data-ttu-id="a719b-135">Datový typ hodnot v poli, na který ukazuje vlastnost `Value`.</span><span class="sxs-lookup"><span data-stu-id="a719b-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="a719b-136">Formáty označené hodnotami `Type` vlastností jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a719b-136">The formats indicated by the `Type` property values are shown in the following table:</span></span>

|<span data-ttu-id="a719b-137">Číselná hodnota</span><span class="sxs-lookup"><span data-stu-id="a719b-137">Numeric value</span></span>|<span data-ttu-id="a719b-138">Popis</span><span class="sxs-lookup"><span data-stu-id="a719b-138">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="a719b-139">první</span><span class="sxs-lookup"><span data-stu-id="a719b-139">1</span></span>|<span data-ttu-id="a719b-140">`Byte`</span><span class="sxs-lookup"><span data-stu-id="a719b-140">A `Byte`</span></span>|
|<span data-ttu-id="a719b-141">odst</span><span class="sxs-lookup"><span data-stu-id="a719b-141">2</span></span>|<span data-ttu-id="a719b-142">Pole objektů `Byte` kódovaných jako ASCII</span><span class="sxs-lookup"><span data-stu-id="a719b-142">An array of `Byte` objects encoded as ASCII</span></span>|
|<span data-ttu-id="a719b-143">3</span><span class="sxs-lookup"><span data-stu-id="a719b-143">3</span></span>|<span data-ttu-id="a719b-144">16bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="a719b-144">A 16-bit integer</span></span>|
|<span data-ttu-id="a719b-145">4</span><span class="sxs-lookup"><span data-stu-id="a719b-145">4</span></span>|<span data-ttu-id="a719b-146">32 celé číslo</span><span class="sxs-lookup"><span data-stu-id="a719b-146">A 32-bit integer</span></span>|
|<span data-ttu-id="a719b-147">5</span><span class="sxs-lookup"><span data-stu-id="a719b-147">5</span></span>|<span data-ttu-id="a719b-148">Pole dvou `Byte` objektů, které reprezentují racionální číslo</span><span class="sxs-lookup"><span data-stu-id="a719b-148">An array of two `Byte` objects that represent a rational number</span></span>|
|<span data-ttu-id="a719b-149">6</span><span class="sxs-lookup"><span data-stu-id="a719b-149">6</span></span>|<span data-ttu-id="a719b-150">Nepoužívá se</span><span class="sxs-lookup"><span data-stu-id="a719b-150">Not used</span></span>|
|<span data-ttu-id="a719b-151">čl</span><span class="sxs-lookup"><span data-stu-id="a719b-151">7</span></span>|<span data-ttu-id="a719b-152">Nedefinované</span><span class="sxs-lookup"><span data-stu-id="a719b-152">Undefined</span></span>|
|<span data-ttu-id="a719b-153">8</span><span class="sxs-lookup"><span data-stu-id="a719b-153">8</span></span>|<span data-ttu-id="a719b-154">Nepoužívá se</span><span class="sxs-lookup"><span data-stu-id="a719b-154">Not used</span></span>|
|<span data-ttu-id="a719b-155">9</span><span class="sxs-lookup"><span data-stu-id="a719b-155">9</span></span>|`SLong`|
|<span data-ttu-id="a719b-156">10pruhový</span><span class="sxs-lookup"><span data-stu-id="a719b-156">10</span></span>|`SRational`|

## <a name="example"></a><span data-ttu-id="a719b-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="a719b-157">Example</span></span>
  
<span data-ttu-id="a719b-158">Následující příklad kódu načte a zobrazí sedm částí metadat v souboru `FakePhoto.jpg`.</span><span class="sxs-lookup"><span data-stu-id="a719b-158">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="a719b-159">Druhá položka vlastnosti (index 1) v seznamu má <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (výrobce zařízení) a <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (bajtové pole s kódováním ASCII).</span><span class="sxs-lookup"><span data-stu-id="a719b-159">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="a719b-160">V příkladu kódu se zobrazí hodnota této položky vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a719b-160">The code example displays the value of that property item.</span></span>

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

<span data-ttu-id="a719b-161">Kód vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="a719b-161">The code produces output similar to the following:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="a719b-162">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a719b-162">Compiling the Code</span></span>

<span data-ttu-id="a719b-163">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr obslužné rutiny události <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="a719b-163">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="a719b-164">Zpracujte událost <xref:System.Windows.Forms.Control.Paint> formuláře a vložte tento kód do obslužné rutiny události Paint.</span><span class="sxs-lookup"><span data-stu-id="a719b-164">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="a719b-165">Je nutné nahradit `FakePhoto.jpg` názvem bitové kopie a cestou platným ve vašem systému a importovat obor názvů `System.Drawing.Imaging`.</span><span class="sxs-lookup"><span data-stu-id="a719b-165">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="a719b-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a719b-166">See also</span></span>

- [<span data-ttu-id="a719b-167">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="a719b-167">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="a719b-168">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="a719b-168">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
