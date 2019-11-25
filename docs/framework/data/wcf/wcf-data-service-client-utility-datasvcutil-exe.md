---
title: Nástroj klienta WCF Data Services (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: de260e1a6b58fdbac1a2f0f40c7ec2e50b13644e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975089"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Nástroj klienta WCF Data Services (DataSvcUtil.exe)

DataSvcUtil. exe je nástroj příkazového řádku, který poskytuje WCF Data Services, který využívá informační kanál OData (Open Data Protocol) a generuje třídy služby data klienta, které jsou potřebné pro přístup k datové službě z klientské aplikace .NET Framework. Tento nástroj může generovat datové třídy pomocí následujících zdrojů metadat:

- Kořenový identifikátor URI datové služby. Nástroj požádá o dokument metadat služby, který popisuje datový model zpřístupněný datovou službou. Další informace najdete v [dokumentu metadata služby OData:](https://go.microsoft.com/fwlink/?LinkId=186070).

- Soubor datového modelu (. CSDL) definovaný pomocí jazyka CSDL (konceptuální schéma Definition Language), jak je definováno ve specifikaci [\[MC-csdl\]: koncepční specifikace formátu definičního souboru schématu](https://go.microsoft.com/fwlink/?LinkID=159072) .

- Soubor. edmx vytvořený pomocí model EDM (Entity Data Model)ch nástrojů, které jsou k dispozici v Entity Framework. Další informace najdete v tématu [\[MC-EDMX\]: model EDM (Entity Data Model) pro specifikaci formátu balíčku Data Services](https://go.microsoft.com/fwlink/?LinkID=178833) .

Další informace najdete v tématu [Postup: ruční generování tříd klientských datových služeb](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).

Nástroj DataSvcUtil. exe je nainstalován v adresáři .NET Framework. V mnoha případech se nachází v *C:\Windows\Microsoft.NET\Framework\v4.0*. Pro 64 systémy se nachází v *C:\Windows\Microsoft.NET\Framework64\v4.0*. K nástroji DataSvcUtil. exe můžete získat přístup také z Developer Command Prompt pro Visual Studio.

## <a name="syntax"></a>Syntaxe

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Parametry

|Možnost|Popis|
|------------|-----------------|
|`/dataservicecollection`|Určuje, že kód potřebný k vázání objektů k ovládacím prvkům je také vygenerován.|
|`/help`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|
|*soubor\<`/in:` >*|Určuje soubor. csdl nebo. edmx nebo adresář, kde se nachází soubor.|
|`/language:`[VB&#124;CSharp]|Určuje jazyk pro vygenerované soubory zdrojového kódu. Výchozí jazyk je C#.|
|`/nologo`|Potlačí zobrazení zprávy o autorských právech.|
|*soubor\<`/out:` >*|Určuje název souboru se zdrojovým kódem, který obsahuje vygenerované třídy datové služby klienta.|
|*řetězec\<`/uri:` >*|Identifikátor URI datového kanálu OData|
|`/version:`[1,0&#124;2,0]|Určuje nejvyšší přijatou verzi OData. Verze je určena na základě atributu `DataServiceVersion` prvku DataService v vrácených metadatech datové služby. Další informace najdete v tématu [Správa verzí datových služeb](data-service-versioning-wcf-data-services.md). Pokud zadáte parametr `/dataservicecollection`, je nutné zadat také `/version:2.0`, aby bylo možné datovou vazbu povolit.|

## <a name="see-also"></a>Viz také:

- [Generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md)
- [Postupy: Přidání odkazu na datovou službu](how-to-add-a-data-service-reference-wcf-data-services.md)
