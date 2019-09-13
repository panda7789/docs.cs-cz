---
title: 'Postupy: Ruční generování tříd klientských datových služeb (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: f8d99213a1ef98c48855ba9f561f87a800768c89
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894294"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Postupy: Ruční generování tříd klientských datových služeb (WCF Data Services)
WCF Data Services se integruje se sadou Visual Studio, aby vám umožnila automatické generování tříd klientské datové služby při použití dialogového okna **Přidat odkaz na službu** k přidání odkazu na datovou službu v projektu sady Visual Studio. Další informace najdete v tématu [jak: Přidejte odkaz](how-to-add-a-data-service-reference-wcf-data-services.md)na datovou službu. Můžete také ručně vygenerovat stejné třídy datové služby klienta pomocí nástroje `DataSvcUtil.exe`pro generování kódu. Tento nástroj, který je součástí WCF Data Services, generuje .NET Framework třídy z definice datové služby. Lze ji také použít ke generování tříd datové služby ze souboru koncepčního modelu (. CSDL) a ze souboru. edmx, který představuje model Entity Framework v projektu sady Visual Studio.

 Příklad v tomto tématu vytvoří klientské třídy datové služby založené na ukázkové datové službě Northwind. Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md). Některé příklady v tomto tématu vyžadují koncepční soubor modelu pro model Northwind. Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe. Některé příklady v tomto tématu vyžadují soubor. edmx pro model Northwind. Další informace najdete v tématu [Přehled souborů. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).

### <a name="to-generate-c-classes-that-support-data-binding"></a>Generovat C# třídy, které podporují datové vazby

- Na příkazovém řádku spusťte následující příkaz bez konců řádků:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Je nutné nahradit hodnotu `/uri:` dodanou parametr identifikátorem URI vaší instance služby ukázkových dat Northwind.

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Generování Visual Basic třídy, které podporují datové vazby

- Na příkazovém řádku spusťte následující příkaz bez konců řádků:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Je nutné nahradit hodnotu dodanou `/uri:` parametr identifikátorem URI vaší instance služby ukázkových dat Northwind.

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Generování C# tříd založených na identifikátoru URI služby

- Na příkazovém řádku spusťte následující příkaz bez konců řádků:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Je nutné nahradit hodnotu `/uri:` dodanou parametr identifikátorem URI vaší instance služby ukázkových dat Northwind.

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Generování tříd Visual Basic na základě identifikátoru URI služby

- Na příkazovém řádku spusťte následující příkaz bez konců řádků:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Je nutné nahradit hodnotu dodanou `/uri:` parametr identifikátorem URI vaší instance služby ukázkových dat Northwind.

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Generování C# tříd založených na souboru koncepčního modelu (CSDL)

- Na příkazovém řádku spusťte následující příkaz bez konců řádků:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Vygenerování Visual Basic třídy založené na souboru koncepčního modelu (CSDL)

- Na příkazovém řádku spusťte následující příkaz bez konců řádků:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Generování C# tříd založených na souboru. edmx

- Na příkazovém řádku spusťte následující příkaz bez konců řádků:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Generování Visual Basic tříd založených na souboru. edmx

- Na příkazovém řádku spusťte následující příkaz bez konců řádků:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>Viz také:

- [Generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md)
- [Postupy: Přidat odkaz na datovou službu](how-to-add-a-data-service-reference-wcf-data-services.md)
- [Nástroj klienta WCF Data Services (DataSvcUtil.exe)](wcf-data-service-client-utility-datasvcutil-exe.md)
