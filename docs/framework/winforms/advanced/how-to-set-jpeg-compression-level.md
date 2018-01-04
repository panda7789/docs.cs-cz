---
title: "Postupy: Nastavení úrovně komprese JPEG"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02e417fbcdb68e114ea0fc7afad7c22f6b2fdae9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-jpeg-compression-level"></a>Postupy: Nastavení úrovně komprese JPEG
Můžete změnit parametry bitové kopie, když uložit obrázek na disk na minimální velikost souboru nebo zvýšení jeho kvality. Kvalitu obrazu JPEG můžete upravit změnou jeho úroveň komprese. K určení úrovně komprese při ukládání ve formátu JPEG, musíte vytvořit <xref:System.Drawing.Imaging.EncoderParameters> objektu a předejte ji do <xref:System.Drawing.Image.Save%2A> metodu <xref:System.Drawing.Image> třídy. Inicializace <xref:System.Drawing.Imaging.EncoderParameters> objektu tak, že IT oddělení má pole, které se skládá z jednoho <xref:System.Drawing.Imaging.EncoderParameter>. Když vytvoříte <xref:System.Drawing.Imaging.EncoderParameter>, zadejte <xref:System.Drawing.Imaging.Encoder.Quality> kodér a úroveň požadované komprese.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří <xref:System.Drawing.Imaging.EncoderParameter> objekt a uloží tři JPEG – obrázky. Každý obrázek JPEG se uloží s úrovní jinou kvalitu změnou `long` hodnotu předanou <xref:System.Drawing.Imaging.EncoderParameter> konstruktor. Úrovně kvality 0 odpovídá největší komprese a úrovně kvality 100 odpovídá minimálně komprese.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
-   Soubor obrázku, který je pojmenován `TestPhoto.jpg` a v umístění **c:\\**.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Určení parametrů podporovaných kodérem](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 [Typy rastrových obrázků](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [Použití kodérů a dekodérů ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
