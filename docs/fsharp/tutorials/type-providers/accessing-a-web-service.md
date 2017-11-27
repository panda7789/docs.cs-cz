---
title: "Návod - přístup k webové službě s použitím zprostředkovatelů typů (F #)"
description: "Naučte se používat pro přístup k službě WSDL webové služby popis Language (WSDL) typ zprostředkovatele, který je k dispozici v F # 3.0."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 06d955033d465cf58af05f483d21175f90d1777a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a>Návod: Přístup k webové službě s použitím zprostředkovatelů typů

> [!NOTE]
Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.  V tématu [FSharp.Data](http://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.

> [!NOTE]
Rozhraní API referenčních odkazů se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Tento návod ukazuje, jak použít typ poskytovatele služeb popis jazyka WSDL (Web), který je k dispozici v F # 3.0 pro přístup k službě WSDL. V dalších jazycích .NET generovat kód pro přístup k webové službě pomocí volání svcutil.exe nebo přidáním webový odkaz v například C# projektu získat chcete volat svcutil.exe pro vás Visual Studio. V jazyce F # máte možnost navíc pomocí zprostředkovatele typu WSDL, takže co nejdříve můžete napsat kód, který vytváří wsdlservice – typ, typy jsou generovány a bude k dispozici. Tento proces závisí na službě, který je k dispozici při psaní kódu.

Tento návod ukazuje následující úlohy. V tomto pořadí návod úspěšná, musíte provést je:


- Vytvoření projektu
<br />

- Konfigurace poskytovatele typu
<br />

- Volání webové služby a zpracování výsledků
<br />


## <a name="creating-the-project"></a>Vytvoření projektu
V kroku vytvořte projekt a přidejte příslušné odkazy na pro použití poskytovatele typu WSDL.


#### <a name="to-create-and-set-up-an-f-project"></a>Postup vytvoření a nastavení projektu jazyka F#

1. Otevřete nový projekt konzolové aplikace v F #.
<br />

2. V **Průzkumníku řešení**, otevřete místní nabídky projektu **odkaz** uzel a potom zvolte **přidat odkaz na**.
<br />

3. V **sestavení** oblasti, zvolte **Framework**a potom v seznamu dostupných sestavení, zvolte **System.Runtime.Serialization** a  **System.ServiceModel**.
<br />

4. V **sestavení** oblasti, zvolte **rozšíření**.
<br />

5. V seznamu dostupných sestavení, zvolte **FSharp.Data.TypeProviders**a potom zvolte **OK** tlačítko přidáte odkazy na tyto sestavení.
<br />

## <a name="configuring-the-type-provider"></a>Konfigurace poskytovatele typu
V tomto kroku použijete ke generování typy pro webovou službu TerraServer WSDL typ zprostředkovatele.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Postup konfigurace poskytovatele typu a generování typů

1. Přidejte následující řádek kódu otevřete obor názvů zprostředkovatele typu.
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. Přidejte následující řádek kódu pro vyvolání typu zprostředkovatele s webovou službou. V tomto příkladu použijte TerraServer webové služby.
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "http://terraserver-usa.com/TerraService2.asmx?WSDL" http://msrmaps.com/TerraService2.asmx?WSDL">
```

  Červenou vlnovkou se zobrazí pod tento řádek kódu URI služby je chybný nebo pokud samotné služby je vypnutý nebo není provádění. Pokud zadáte odkaz na kód, chybová zpráva popisuje problém. Stejné informace ve můžete najít **seznam chyb** okno nebo v **výstup – okno** po sestavení.
<br />  Existují dva způsoby ke specifikaci nastavení konfigurace pro připojení WSDL pomocí souboru app.config pro projekt nebo pomocí statické typ parametry v deklaraci typu poskytovatele. Svcutil.exe můžete použít ke generování souboru příslušné konfigurace – elementy. Další informace o používání svcutil.exe generovat informace o konfiguraci pro webové služby najdete v tématu [ServiceModel Metadata Utility Tool &#40; Svcutil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx). Úplný popis Parametry statické typu pro typ zprostředkovatele WSDL, najdete v části [wsdlservice – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a>Volání webové služby a zpracování výsledků
Každý webová služba má vlastní sadu typů, které jsou použity jako parametry pro jeho volání metody. V tomto kroku připravit tyto parametry, volání metody webové a zpracovat informace, které vrátí.


#### <a name="to-call-the-web-service-and-process-the-results"></a>Volání webové služby a zpracovat výsledky

1. Webová služba může vypršení časového limitu nebo přestane fungovat, takže by měla obsahovat volání webové služby v bloku zpracování výjimek. Následující kód pokusit se získat data z webové služby zápisu.
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

Všimněte si, že můžete vytvořit datové typy, které jsou potřebné pro webovou službu, jako například **místní** a **umístění**, jako typ vnořené typy pod wsdlservice – **TerraService**.
<br />


## <a name="see-also"></a>Viz také
[Wsdlservice – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[Zprostředkovatelé typů](index.md)
