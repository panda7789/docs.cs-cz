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
ms.openlocfilehash: 6c02f7e5744828fd8eddc88be8d7da28f3bc2a2a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505774"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="9cf63-102">Postupy: Čtení metadat obrázku</span><span class="sxs-lookup"><span data-stu-id="9cf63-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="9cf63-103">Některé soubory obrázku obsahují metadata, která si můžete přečíst určit funkce bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="9cf63-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="9cf63-104">Digitální fotografie může například obsahovat metadata, která si můžete přečíst k určení značku a model fotoaparátu/kamery, používá k zachycení bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="9cf63-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="9cf63-105">Pomocí GDI + existující metadata mohou číst a můžete je zapsat také nová metadata do souborů obrázků.</span><span class="sxs-lookup"><span data-stu-id="9cf63-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 <span data-ttu-id="9cf63-106">Rozhraní GDI + ukládá jednotlivé část metadata <xref:System.Drawing.Imaging.PropertyItem> objektu.</span><span class="sxs-lookup"><span data-stu-id="9cf63-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="9cf63-107">Si můžete přečíst <xref:System.Drawing.Image.PropertyItems%2A> vlastnost <xref:System.Drawing.Image> objektu k načtení všechna metadata ze souboru.</span><span class="sxs-lookup"><span data-stu-id="9cf63-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="9cf63-108"><xref:System.Drawing.Image.PropertyItems%2A> Vlastnost vrací pole <xref:System.Drawing.Imaging.PropertyItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="9cf63-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="9cf63-109">A <xref:System.Drawing.Imaging.PropertyItem> objekt má následující čtyři vlastnosti: `Id`, `Value`, `Len`, a `Type`.</span><span class="sxs-lookup"><span data-stu-id="9cf63-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="9cf63-110">Id</span><span class="sxs-lookup"><span data-stu-id="9cf63-110">Id</span></span>  
 <span data-ttu-id="9cf63-111">Značka, která identifikuje položku metadat.</span><span class="sxs-lookup"><span data-stu-id="9cf63-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="9cf63-112">Některé hodnoty, které je možné přiřadit <xref:System.Drawing.Imaging.PropertyItem.Id%2A> jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9cf63-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="9cf63-113">Šestnáctková hodnota</span><span class="sxs-lookup"><span data-stu-id="9cf63-113">Hexadecimal value</span></span>|<span data-ttu-id="9cf63-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9cf63-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="9cf63-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="9cf63-115">0x0320</span></span><br /><br /> <span data-ttu-id="9cf63-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="9cf63-116">0x010F</span></span><br /><br /> <span data-ttu-id="9cf63-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="9cf63-117">0x0110</span></span><br /><br /> <span data-ttu-id="9cf63-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="9cf63-118">0x9003</span></span><br /><br /> <span data-ttu-id="9cf63-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="9cf63-119">0x829A</span></span><br /><br /> <span data-ttu-id="9cf63-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="9cf63-120">0x5090</span></span><br /><br /> <span data-ttu-id="9cf63-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="9cf63-121">0x5091</span></span>|<span data-ttu-id="9cf63-122">Název bitové kopie</span><span class="sxs-lookup"><span data-stu-id="9cf63-122">Image title</span></span><br /><br /> <span data-ttu-id="9cf63-123">Výrobce OEM</span><span class="sxs-lookup"><span data-stu-id="9cf63-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="9cf63-124">Model zařízení</span><span class="sxs-lookup"><span data-stu-id="9cf63-124">Equipment model</span></span><br /><br /> <span data-ttu-id="9cf63-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="9cf63-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="9cf63-126">Chcete zkrátit dobu expozice EXIF</span><span class="sxs-lookup"><span data-stu-id="9cf63-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="9cf63-127">Tabulka světlosti</span><span class="sxs-lookup"><span data-stu-id="9cf63-127">Luminance table</span></span><br /><br /> <span data-ttu-id="9cf63-128">Chrominance tabulky</span><span class="sxs-lookup"><span data-stu-id="9cf63-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="9cf63-129">Value</span><span class="sxs-lookup"><span data-stu-id="9cf63-129">Value</span></span>  
 <span data-ttu-id="9cf63-130">Pole hodnot.</span><span class="sxs-lookup"><span data-stu-id="9cf63-130">An array of values.</span></span> <span data-ttu-id="9cf63-131">Formát hodnoty je určeno <xref:System.Drawing.Imaging.PropertyItem.Type%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9cf63-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="9cf63-132">Délka</span><span class="sxs-lookup"><span data-stu-id="9cf63-132">Len</span></span>  
 <span data-ttu-id="9cf63-133">Délka (v bajtech) pole hodnot, na které odkazují <xref:System.Drawing.Imaging.PropertyItem.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9cf63-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="9cf63-134">type</span><span class="sxs-lookup"><span data-stu-id="9cf63-134">Type</span></span>  
 <span data-ttu-id="9cf63-135">Datový typ hodnoty v poli na které odkazují `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9cf63-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="9cf63-136">Formáty indikován `Type` v následující tabulce jsou uvedeny hodnoty vlastností</span><span class="sxs-lookup"><span data-stu-id="9cf63-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="9cf63-137">Číselná hodnota</span><span class="sxs-lookup"><span data-stu-id="9cf63-137">Numeric value</span></span>|<span data-ttu-id="9cf63-138">Popis</span><span class="sxs-lookup"><span data-stu-id="9cf63-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="9cf63-139">1</span><span class="sxs-lookup"><span data-stu-id="9cf63-139">1</span></span>|<span data-ttu-id="9cf63-140">A `Byte`</span><span class="sxs-lookup"><span data-stu-id="9cf63-140">A `Byte`</span></span>|  
|<span data-ttu-id="9cf63-141">2</span><span class="sxs-lookup"><span data-stu-id="9cf63-141">2</span></span>|<span data-ttu-id="9cf63-142">Pole `Byte` objekty kódováním ASCII</span><span class="sxs-lookup"><span data-stu-id="9cf63-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="9cf63-143">3</span><span class="sxs-lookup"><span data-stu-id="9cf63-143">3</span></span>|<span data-ttu-id="9cf63-144">16bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="9cf63-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="9cf63-145">4</span><span class="sxs-lookup"><span data-stu-id="9cf63-145">4</span></span>|<span data-ttu-id="9cf63-146">32bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="9cf63-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="9cf63-147">5</span><span class="sxs-lookup"><span data-stu-id="9cf63-147">5</span></span>|<span data-ttu-id="9cf63-148">Pole dvou `Byte` objekty, které představují racionální číslo</span><span class="sxs-lookup"><span data-stu-id="9cf63-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="9cf63-149">6</span><span class="sxs-lookup"><span data-stu-id="9cf63-149">6</span></span>|<span data-ttu-id="9cf63-150">Nepoužívá se</span><span class="sxs-lookup"><span data-stu-id="9cf63-150">Not used</span></span>|  
|<span data-ttu-id="9cf63-151">7</span><span class="sxs-lookup"><span data-stu-id="9cf63-151">7</span></span>|<span data-ttu-id="9cf63-152">Nedefinováno</span><span class="sxs-lookup"><span data-stu-id="9cf63-152">Undefined</span></span>|  
|<span data-ttu-id="9cf63-153">8</span><span class="sxs-lookup"><span data-stu-id="9cf63-153">8</span></span>|<span data-ttu-id="9cf63-154">Nepoužívá se</span><span class="sxs-lookup"><span data-stu-id="9cf63-154">Not used</span></span>|  
|<span data-ttu-id="9cf63-155">9</span><span class="sxs-lookup"><span data-stu-id="9cf63-155">9</span></span>|`SLong`|  
|<span data-ttu-id="9cf63-156">10</span><span class="sxs-lookup"><span data-stu-id="9cf63-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="9cf63-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cf63-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9cf63-158">Popis</span><span class="sxs-lookup"><span data-stu-id="9cf63-158">Description</span></span>  
 <span data-ttu-id="9cf63-159">Následující příklad kódu načte a zobrazí sedmi částí metadat v souboru `FakePhoto.jpg`.</span><span class="sxs-lookup"><span data-stu-id="9cf63-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="9cf63-160">Druhá položka vlastnosti (index 1) v seznamu má <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (výrobce) a <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (pole bajtů s kódováním ASCII).</span><span class="sxs-lookup"><span data-stu-id="9cf63-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="9cf63-161">Příklad kódu zobrazí hodnotu této vlastnosti položky.</span><span class="sxs-lookup"><span data-stu-id="9cf63-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="9cf63-162">Kód vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="9cf63-162">The code produces output similar to the following:</span></span>  
 
```
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
  
### <a name="code"></a><span data-ttu-id="9cf63-163">Kód</span><span class="sxs-lookup"><span data-stu-id="9cf63-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9cf63-164">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9cf63-164">Compiling the Code</span></span>  
 <span data-ttu-id="9cf63-165">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="9cf63-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="9cf63-166">Zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí a vložte tento kód do obslužné rutiny události Malování.</span><span class="sxs-lookup"><span data-stu-id="9cf63-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="9cf63-167">Je třeba nahradit `FakePhoto.jpg` název image a cesta platné na systém a import `System.Drawing.Imaging` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9cf63-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf63-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cf63-168">See also</span></span>

- [<span data-ttu-id="9cf63-169">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="9cf63-169">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="9cf63-170">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="9cf63-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
