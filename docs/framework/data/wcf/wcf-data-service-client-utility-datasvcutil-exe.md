---
title: Nástroj klienta WCF Data Services (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 97e9502176e0cc2f36d67ee3dc8e8d0739a009b2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790190"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Nástroj klienta WCF Data Services (DataSvcUtil.exe)

DataSvcUtil. exe je nástroj příkazového řádku, který poskytuje WCF Data Services, který využívá [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informační kanál a generuje třídy klientské datové služby, které jsou potřebné pro přístup k datové službě z klientské aplikace .NET Framework. Tento nástroj může generovat datové třídy pomocí následujících zdrojů metadat:

- Kořenový identifikátor URI datové služby. Nástroj požádá o dokument metadat služby, který popisuje datový model zpřístupněný datovou službou. Další informace najdete v tématu [OData: Dokument](https://go.microsoft.com/fwlink/?LinkId=186070)metadat služby

- Soubor datového modelu (. CSDL) definovaný pomocí jazyka CSDL (konceptuální schéma Definition Language), jak je definováno ve [ \[MC-CSDL\]: Specifikace formátu](https://go.microsoft.com/fwlink/?LinkID=159072) definičního souboru koncepčního schématu

- Soubor. edmx vytvořený pomocí model EDM (Entity Data Model)ch nástrojů, které jsou k dispozici v Entity Framework. Další informace najdete v tématu [ \[MC-EDMX\]: Model EDM (Entity Data Model) pro specifikaci formátu](https://go.microsoft.com/fwlink/?LinkID=178833) balíčku Data Services.

Další informace najdete v tématu [jak: Ručně vygenerujte třídy](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)datové služby klienta.

Nástroj DataSvcUtil. exe je nainstalován v adresáři .NET Framework. V mnoha případech se nachází v *C:\Windows\Microsoft.NET\Framework\v4.0*. Pro 64 systémy se nachází v *C:\Windows\Microsoft.NET\Framework64\v4.0*. K nástroji DataSvcUtil. exe můžete získat přístup také z Developer Command Prompt pro Visual Studio.

## <a name="syntax"></a>Syntaxe

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Parametry

|Možnost|Popis|
|------------|-----------------|
|`/dataservicecollection`|Určuje, že kód potřebný k vázání objektů k ovládacím prvkům je také vygenerován.|
|`/help`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|
|`/in:` *>\<souboru*|Určuje soubor. csdl nebo. edmx nebo adresář, kde se nachází soubor.|
|`/language:`[VB&#124;CSharp]|Určuje jazyk pro vygenerované soubory zdrojového kódu. Výchozí jazyk je C#.|
|`/nologo`|Potlačí zobrazení zprávy o autorských právech.|
|`/out:` *>\<souboru*|Určuje název souboru se zdrojovým kódem, který obsahuje vygenerované třídy datové služby klienta.|
|`/uri:` *>\<řetězců*|Identifikátor URI datového kanálu OData|
|`/version:`[1.0&#124;2.0]|Určuje nejvyšší přijatou verzi OData. Verze je určena v závislosti na `DataServiceVersion` atributu prvku DataService v vrácených metadatech datové služby. Další informace najdete v tématu [Správa verzí datových služeb](data-service-versioning-wcf-data-services.md). Pokud zadáte `/dataservicecollection` parametr, je nutné také zadat `/version:2.0` , aby bylo možné datové vazby povolit.|

## <a name="see-also"></a>Viz také:

- [Generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md)
- [Postupy: Přidat odkaz na datovou službu](how-to-add-a-data-service-reference-wcf-data-services.md)
