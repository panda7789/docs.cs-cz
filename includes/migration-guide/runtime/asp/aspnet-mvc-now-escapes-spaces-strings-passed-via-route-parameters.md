---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803218"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC nyní uniká mezery v řetězcích předávaných parametry trasy

|   |   |
|---|---|
|Podrobnosti|Aby bylo možné vyhovět RFC 2396, mezery v trasách trasy jsou nyní uvozeny při vyplnění parametrů akce z trasy. Takže vzhledem <code>/controller/action/some data</code> k tomu, <code>/controller/action/{data}</code> že <code>some data</code> by dříve odpovídat postupu <code>some%20data</code> a poskytnout jako parametr data, bude nyní poskytovat místo.|
|Návrh|Kód by měl být aktualizován na unescape parametry řetězce z trasy. Pokud je potřeba původní identifikátor URI, lze <xref:System.Net.HttpWebRequest.RequestUri>k němu přistupovat pomocí . OriginalString API.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
