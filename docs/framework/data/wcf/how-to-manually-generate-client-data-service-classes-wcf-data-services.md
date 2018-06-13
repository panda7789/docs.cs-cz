---
title: 'Postupy: ruční generují třídy služby dat klienta (služby WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 24d19f10e025b765cfc7df73ba80d223fbfa8074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358991"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Postupy: ruční generují třídy služby dat klienta (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] se integruje s Visual Studio umožňují automaticky generovat třídy služeb klienta data při použití **přidat odkaz na službu** dialogové okno Přidat odkaz na datové služby v projektu sady Visual Studio. Další informace najdete v tématu [postupy: Přidání odkazu na službu Data](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md). Stejné třídy služby dat klienta lze vytvořit také ručně pomocí nástroje generování kódu `DataSvcUtil.exe`. Tento nástroj, který je součástí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vygeneruje třídy rozhraní .NET Framework z definici datové služby. Také se použít pro generování třídy služeb dat ze souboru konceptuálního modelu (.csdl) a ze souboru .edmx, který představuje model Entity Framework v projektu sady Visual Studio.  
  
 V příkladu v tomto tématu se vytvoří třídy služeb dat klienta založené na službě Northwind ukázková data. Tato služba se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Některé příklady v tomto tématu vyžadují soubor konceptuálního modelu pro Northwind model. Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a mapování soubory](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md). Některé příklady v tomto tématu vyžadují soubor EDMX Northwind modelu. Další informace najdete v tématu [.edmx souboru přehled](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a>Vygenerovat třídy jazyka C#, které podporují datová vazba  
  
-   Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Hodnota zadaná pro musí nahradit `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Vygenerovat třídy jazyka Visual Basic, které podporují datová vazba  
  
-   Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Hodnota zadaná pro musí nahradit `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Vygenerovat C# třídy založené na URI služby  
  
-   Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Hodnota zadaná pro musí nahradit `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Vygenerovat URI služby podle třídy jazyka Visual Basic  
  
-   Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Hodnota zadaná pro musí nahradit `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Ke generování třídy jazyka C# na základě souboru konceptuálního modelu (CSDL)  
  
-   Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Vygenerovat na základě souboru konceptuálního modelu (CSDL) třídy jazyka Visual Basic  
  
-   Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Ke generování třídy jazyka C# na základě souboru EDMX  
  
-   Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Vygenerovat na základě souboru .edmx třídy jazyka Visual Basic  
  
-   Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a>Viz také  
 [Generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [Postupy: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [Nástroj klienta WCF Data Services (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
