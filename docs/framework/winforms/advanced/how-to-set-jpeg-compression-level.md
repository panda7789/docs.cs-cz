---
title: 'Postupy: Nastavení úrovně komprese JPEG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
ms.openlocfilehash: de9dce1b3c15070fda268c430ce5da641efef6f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003883"
---
# <a name="how-to-set-jpeg-compression-level"></a><span data-ttu-id="31fca-102">Postupy: Nastavení úrovně komprese JPEG</span><span class="sxs-lookup"><span data-stu-id="31fca-102">How to: Set JPEG Compression Level</span></span>
<span data-ttu-id="31fca-103">Můžete chtít upravit parametry bitovou kopii při uložení image na disk na minimální velikost souboru nebo zlepšení jeho kvality.</span><span class="sxs-lookup"><span data-stu-id="31fca-103">You may want to modify the parameters of an image when you save the image to disk to minimize the file size or improve its quality.</span></span> <span data-ttu-id="31fca-104">Kvalita obrázku JPEG můžete upravit tak, že upravíte jejich úroveň komprese.</span><span class="sxs-lookup"><span data-stu-id="31fca-104">You can adjust the quality of a JPEG image by modifying its compression level.</span></span> <span data-ttu-id="31fca-105">Chcete-li určit úroveň komprese při ukládání ve formátu JPEG, musíte vytvořit <xref:System.Drawing.Imaging.EncoderParameters> objektu a předejte ji do <xref:System.Drawing.Image.Save%2A> metodu <xref:System.Drawing.Image> třídy.</span><span class="sxs-lookup"><span data-stu-id="31fca-105">To specify the compression level when you save a JPEG image, you must create an <xref:System.Drawing.Imaging.EncoderParameters> object and pass it to the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="31fca-106">Inicializovat <xref:System.Drawing.Imaging.EncoderParameters> objektu tak, že je pole, které se skládá z jednoho <xref:System.Drawing.Imaging.EncoderParameter>.</span><span class="sxs-lookup"><span data-stu-id="31fca-106">Initialize the <xref:System.Drawing.Imaging.EncoderParameters> object so that it has an array that consists of one <xref:System.Drawing.Imaging.EncoderParameter>.</span></span> <span data-ttu-id="31fca-107">Při vytváření <xref:System.Drawing.Imaging.EncoderParameter>, zadejte <xref:System.Drawing.Imaging.Encoder.Quality> kodér a úroveň požadované komprese.</span><span class="sxs-lookup"><span data-stu-id="31fca-107">When you create the <xref:System.Drawing.Imaging.EncoderParameter>, specify the <xref:System.Drawing.Imaging.Encoder.Quality> encoder, and the desired compression level.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31fca-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="31fca-108">Example</span></span>  
 <span data-ttu-id="31fca-109">Následující příklad kódu vytvoří <xref:System.Drawing.Imaging.EncoderParameter> objekt a uloží tři obrázků JPEG.</span><span class="sxs-lookup"><span data-stu-id="31fca-109">The following example code creates an <xref:System.Drawing.Imaging.EncoderParameter> object and saves three JPEG images.</span></span> <span data-ttu-id="31fca-110">Každý obrázek JPEG je uložen s různou kvalitu úrovni, tak, že upravíte `long` hodnotu předanou <xref:System.Drawing.Imaging.EncoderParameter> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="31fca-110">Each JPEG image is saved with a different quality level, by modifying the `long` value passed to the <xref:System.Drawing.Imaging.EncoderParameter> constructor.</span></span> <span data-ttu-id="31fca-111">Úroveň kvality 0 odpovídá největší komprese a úroveň kvality 100 odpovídá nejméně komprese.</span><span class="sxs-lookup"><span data-stu-id="31fca-111">A quality level of 0 corresponds to the greatest compression, and a quality level of 100 corresponds to the least compression.</span></span>  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="31fca-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="31fca-112">Compiling the Code</span></span>  
 <span data-ttu-id="31fca-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="31fca-113">This example requires:</span></span>  
  
- <span data-ttu-id="31fca-114">Aplikace modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="31fca-114">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="31fca-115">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="31fca-115">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
- <span data-ttu-id="31fca-116">Soubor obrázku, který je pojmenován `TestPhoto.jpg` a umístění **c:\\**.</span><span class="sxs-lookup"><span data-stu-id="31fca-116">An image file that is named `TestPhoto.jpg` and located at **c:\\**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fca-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31fca-117">See also</span></span>

- [<span data-ttu-id="31fca-118">Postupy: Určuje parametry podporuje kodéru</span><span class="sxs-lookup"><span data-stu-id="31fca-118">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)
- [<span data-ttu-id="31fca-119">Typy rastrových obrázků</span><span class="sxs-lookup"><span data-stu-id="31fca-119">Types of Bitmaps</span></span>](types-of-bitmaps.md)
- [<span data-ttu-id="31fca-120">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="31fca-120">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
