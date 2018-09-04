---
title: 'Postupy: ruční generování tříd klientské datové služby (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 332c04f50e104a5e1c8bd18c05581b6c0472f82f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501318"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Postupy: ruční generování tříd klientské datové služby (WCF Data Services)
Služeb WCF Data Services se integruje se sadou Visual Studio umožňuje automatické generování tříd klientské datové služby, pokud použijete **přidat odkaz na službu** dialogové okno Přidat odkaz na datovou službu v projektu sady Visual Studio. Další informace najdete v tématu [postupy: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md). Můžete také ručně generovat stejný tříd klientské datové služby pomocí nástroje pro generování kódu, `DataSvcUtil.exe`. Tento nástroj, který je součástí služeb WCF Data Services, vygeneruje třídy rozhraní .NET Framework v definici datové služby. Je také slouží ke generování třídy služeb data ze souboru koncepčního modelu (.csdl) a ze souboru EDMX, který představuje model Entity Framework v projektu sady Visual Studio.

 V příkladu v tomto tématu se vytvoří tříd klientské datové služby založené na vzorku datová služba Northwind. Tato služba se vytvoří při dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Příklady v tomto tématu vyžadují souboru koncepčního modelu pro Northwind model. Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a souborů mapování](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md). Příklady v tomto tématu vyžadují soubor .edmx pro Northwind model. Další informace najdete v tématu [edmx soubor přehled](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).

### <a name="to-generate-c-classes-that-support-data-binding"></a>Ke generování třídy jazyka C#, které podporují vytváření datových vazeb

-   Na příkazovém řádku spusťte následující příkaz bez konce řádků:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Je třeba nahradit hodnota předaná `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Ke generování třídy jazyka Visual Basic, které podporují vytváření datových vazeb

-   Na příkazovém řádku spusťte následující příkaz bez konce řádků:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Je třeba nahradit hodnota předaná `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Ke generování třídy jazyka C# založeny na identifikátor URI služby

-   Na příkazovém řádku spusťte následující příkaz bez konce řádků:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Je třeba nahradit hodnota předaná `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Ke generování třídy jazyka Visual Basic založené na identifikátor URI služby

-   Na příkazovém řádku spusťte následující příkaz bez konce řádků:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Je třeba nahradit hodnota předaná `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Ke generování třídy jazyka C# založeny na souboru koncepčního modelu (CSDL)

-   Na příkazovém řádku spusťte následující příkaz bez konce řádků:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Ke generování třídy jazyka Visual Basic konceptuálního modelu souboru (CSDL)

-   Na příkazovém řádku spusťte následující příkaz bez konce řádků:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Ke generování třídy jazyka C# na základě souboru EDMX

-   Na příkazovém řádku spusťte následující příkaz bez konce řádků:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Ke generování třídy jazyka Visual Basic na základě souboru EDMX

-   Na příkazovém řádku spusťte následující příkaz bez konce řádků:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>Viz také

- [Generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [Postupy: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [Nástroj klienta WCF Data Services (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)