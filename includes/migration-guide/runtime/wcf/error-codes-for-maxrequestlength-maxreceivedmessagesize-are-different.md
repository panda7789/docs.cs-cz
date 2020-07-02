---
ms.openlocfilehash: 3aafb14b65f7c0f9e5d77927809547f9d4b96e1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620053"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Kódy chyb pro maxRequestLength nebo třídu maxReceivedMessageSize se liší.

#### <a name="details"></a>Podrobnosti

Zprávy ve webových službách WCF hostované v Internetová informační služba (IIS) nebo ve vývojovém serveru ASP.NET, který překračuje maxRequestLength (v ASP.NET) nebo třídy maxReceivedMessageSize (ve službě WCF), mají rozdílnou chybu codeThe stavový kód HTTP se změnil z 400 (chybný požadavek) na 413 (příliš velký požadavek entity) a zprávy, které překračují buď maxRequestLength nebo nastavení třídy maxReceivedMessageSize, vyvolávají <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> výjimku. To zahrnuje případy, ve kterých je Přenosový režim streamování.

#### <a name="suggestion"></a>Návrh

Tato změna usnadňuje ladění v případech, kde délka zprávy překročí limity povolené ASP.NET nebo WCF. Je třeba upravit jakýkoli kód, který provádí zpracování na základě kódu stavu HTTP 400.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|
