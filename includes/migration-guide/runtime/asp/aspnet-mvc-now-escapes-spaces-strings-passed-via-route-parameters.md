---
ms.openlocfilehash: 7444ddbdd4a7c5f731fba8528ee2334374fc254e
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275097"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC nyní uniká mezery v řetězcích předávaných parametry trasy

|   |   |
|---|---|
|Podrobnosti|Aby bylo možné vyhovět RFC 2396, mezery v trasách trasy jsou nyní uvozeny při vyplnění parametrů akce z trasy. Takže vzhledem <code>/controller/action/some data</code> k tomu, <code>/controller/action/{data}</code> že <code>some data</code> by dříve odpovídat postupu <code>some%20data</code> a poskytnout jako parametr data, bude nyní poskytovat místo.|
|Návrh|Kód by měl být aktualizován na unescape parametry řetězce z trasy. Pokud je potřeba původní identifikátor URI, lze <xref:System.Net.HttpWebRequest.RequestUri>k němu přistupovat pomocí . OriginalString API.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
