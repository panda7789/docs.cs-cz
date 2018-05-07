---
title: Nástroj klienta WCF Data Service (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 3206947d06a1736116674b70e469c20f8f4fca86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Nástroj klienta WCF Data Service (DataSvcUtil.exe)
DataSvcUtil.exe je nástroj příkazového řádku poskytovaný [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , který využívá [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu a vygeneruje třídy klienta dat služby, které jsou potřebné pro přístup ke službě data z klientské aplikace rozhraní .NET Framework. Tento nástroj může generovat datové třídy pomocí následujících zdrojů metadat:  
  
-   Kořen identifikátor URI služby data. Nástroj požadavků dokumentu metadat služby, která popisuje datový model vystavené službu data. Další informace najdete v tématu [OData: dokument metadat služby](http://go.microsoft.com/fwlink/?LinkId=186070).  
  
-   Soubor modelu dat (.csdl) definované za použití definice jazyka konceptuálního schématu (CSDL), jak jsou definovány v [ \[MC CSDL\]: koncepční formátu definičního souboru schématu](http://go.microsoft.com/fwlink/?LinkID=159072) specifikace.  
  
-   Soubor EDMX vytvořili pomocí nástroje datového modelu Entity, které jsou k dispozici rozhraní Entity Framework. Další informace najdete v tématu [ \[MC EDMX\]: datového modelu Entity pro formát dat služby balení](http://go.microsoft.com/fwlink/?LinkID=178833) specifikace.  
  
 Další informace najdete v tématu [postupy: ruční generování dat služby třídy klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
 Nástroj DataSvcUtil.exe se nainstaluje v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adresáře. V mnoha případech je umístěn v C:\Windows\Microsoft.NET\Framework\v4.0. Pro 64bitové systémy je umístěný v C:\Windows\Microsoft.NET\Framework64\v4.0. Můžete také využít nástroj DataSvcUtil.exe z příkazového řádku Visual Studia (klikněte na tlačítko **spustit**, přejděte na příkaz **všechny programy**, přejděte na příkaz **Microsoft Visual Studio 2010**, přejděte na příkaz **nástroje sady Visual Studio**a potom klikněte na **příkazový řádek sady Visual Studio 2010**).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/dataservicecollection`|Určuje, že je kód potřebný k připojení objektů k ovládacím prvkům je vytvořena také.|  
|`/help`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/in:` *\<Soubor >*|Určuje .csdl nebo .edmx soubor nebo adresář, kde je umístěn soubor.|  
|`/language:`[VB&#124;CSharp]|Určuje jazyk pro soubory generované zdrojového kódu. Výchozí hodnoty jazyka C#.|  
|`/nologo`|Potlačí zprávu o autorských právech ze zobrazení.|  
|`/out:` *\<Soubor >*|Určuje název souboru zdrojového kódu, který obsahuje třídy generovaného klienta služby data.|  
|`/uri:` *\<řetězec >*|Identifikátor URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu.|  
|`/version:`[1.0&#124;2.0]|Určuje nejvyšší přijatý verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Verze je určena na základě `DataServiceVersion` atribut elementu DataService v metadatech služby vrácená data. Další informace najdete v tématu [verze datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md). Pokud zadáte `/dataservicecollection` parametru, je nutné také zadat `/version:2.0` povolit datové vazby.|  
  
## <a name="see-also"></a>Viz také  
 [Generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [Postupy: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
