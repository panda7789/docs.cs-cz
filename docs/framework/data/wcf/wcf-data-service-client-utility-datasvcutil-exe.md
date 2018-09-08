---
title: Nástroj klienta WCF Data Service (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 7c9b713571cea3d2c8c5f6511f2cfab7e87b80ee
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189274"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Nástroj klienta WCF Data Service (DataSvcUtil.exe)

DataSvcUtil.exe je nástroj příkazového řádku poskytovaných službou WCF Data Services, která využívá [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] datového kanálu a generuje tříd klientské datové služby, které jsou potřeba pro přístup ke službě data z klientské aplikace rozhraní .NET Framework. Tento nástroj můžete generovat datové třídy pomocí následující zdroje metadat:

-   Kořenovému identifikátoru URI dat služby. Nástroj požaduje metadata dokument služby, který popisuje datový model vystavené datové služby. Další informace najdete v tématu [OData: dokument metadat služby](https://go.microsoft.com/fwlink/?LinkId=186070).

-   Soubor modelu dat (.csdl) definované pomocí Konceptuální schéma definici jazyka (CSDL), jak jsou definovány v [ \[MC CSDL\]: koncepční formátu definičního souboru schématu](https://go.microsoft.com/fwlink/?LinkID=159072) specifikace.

-   Soubor .edmx vytvořené pomocí nástroje modelu Entity Data Model, které jsou k dispozici s rozhraním Entity Framework. Další informace najdete v tématu [ \[MC EDMX\]: Entity Data Model pro formát dat služby balení](https://go.microsoft.com/fwlink/?LinkID=178833) specifikace.

Další informace najdete v tématu [postupy: ruční generování tříd klientské datové služby](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).

Nástroj DataSvcUtil.exe je nainstalován v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adresáře. V mnoha případech je umístěn v *C:\Windows\Microsoft.NET\Framework\v4.0*. Pro 64bitové systémy, je umístěný v *C:\Windows\Microsoft.NET\Framework64\v4.0*. Můžete také DataSvcUtil.exe nástroj dostanete z příkazového řádku pro vývojáře pro sadu Visual Studio.

## <a name="syntax"></a>Syntaxe

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

### <a name="parameters"></a>Parametry

|Možnost|Popis|
|------------|-----------------|
|`/dataservicecollection`|Určuje, že je kód potřebný k vytvoření vazby objektů k ovládacím prvkům také generovány.|
|`/help`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|
|`/in:` *\<Soubor >*|Určuje soubor .csdl nebo edmx nebo adresář, kde je umístěn soubor.|
|`/language:`[VB&#124;CSharp]|Určuje jazyk pro soubory generovaného zdrojového kódu. Výchozí nastavení jazyka C#.|
|`/nologo`|Potlačí zprávu o autorských právech ze zobrazení.|
|`/out:` *\<Soubor >*|Určuje název souboru se zdrojovým kódem, který obsahuje třídy generovaného klienta datové služby.|
|`/uri:` *\<řetězec >*|Identifikátor URI kanálu OData.|
|`/version:`[1.0&#124;2.0]|Určuje nejvyšší přijatá verze protokolu OData. Verze je určena na základě `DataServiceVersion` atribut element DataService v metadatech služby vrácená data. Další informace najdete v tématu [Správa verzí datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md). Pokud zadáte `/dataservicecollection` parametr, musíte zadat také `/version:2.0` datové vazby.|

## <a name="see-also"></a>Viz také

- [Generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [Postupy: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
