---
title: Použití zjednodušených vzorů CQRS a DDD v mikroslužbě
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopení celkového vztahu mezi vzory CQRS a DDD.
ms.date: 10/08/2018
ms.openlocfilehash: f42b553fd30fdffdc6e325b11740fe9162aab7c8
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834305"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Použití zjednodušených vzorů CQRS a DDD v mikroslužbě

CQRS je architektonický model, který odděluje modely pro čtení a zápis dat. [Oddělení příkazů CQS (Term Query Command)](https://martinfowler.com/bliki/CommandQuerySeparation.html) bylo původně definováno v Bertrand Meyer v jeho *konstruktoru orientovaného softwaru na objektech*. Základní nápad je, že je možné rozdělit operace systému na dvě ostře oddělené kategorie:

- Odešle. Tím se vrátí výsledek a nezmění se stav systému, a nejsou k dispozici žádné vedlejší účinky.

- Příkaz. Mění stav systému.

CQS je jednoduchý koncept – jedná se o metody v rámci stejného objektu, které jsou buď dotazy, nebo příkazy. Každá metoda buď vrátí stav nebo stav, ale ne obojí. I jeden objekt vzoru úložiště může odpovídat CQS. CQS se dá považovat za základní princip pro CQRS.

[CQRS (Command and Query Responsibility segregation) (CQRS)](https://martinfowler.com/bliki/CQRS.html) byla zavedena Greg Youngem a silně povýšena UDI Dahan a ostatními. Je založen na principu CQS, i když je podrobnější. Dá se považovat za vzor založený na příkazech a událostech a volitelně na asynchronní zprávy. V mnoha případech se CQRS vztahuje k pokročilejším scénářům, jako je například existence jiné fyzické databáze pro čtení (dotazy) než zápisy (aktualizace). Kromě toho může více vyvíjející systém CQRS implementovat [události](https://martinfowler.com/eaaDev/EventSourcing.html) pro vaši databázi aktualizací, takže byste měli ukládat pouze události do doménového modelu namísto uložení dat aktuálního stavu. Nejedná se ale o přístup k použití v této příručce. používáme nejjednodušší CQRSý přístup, který se skládá jenom ze způsobů oddělení dotazů z příkazů.

Rozdělení aspektu CQRS se dosahuje seskupením operací dotazů v jedné vrstvě a příkazy v jiné vrstvě. Každá vrstva má svůj vlastní datový model (Všimněte si, že model, ne nutně jiná databáze) a je sestavená pomocí vlastní kombinace vzorů a technologií. Důležitější je, že dvě vrstvy můžou být v rámci stejné vrstvy nebo mikroslužby, jako v příkladu (řazení mikroslužeb) používaných v této příručce. Nebo je možné je implementovat na různé mikroslužby nebo procesy, aby je bylo možné optimalizovat a škálovat samostatně, aniž by to ovlivnilo sebe.

CQRS znamená, že mají dva objekty pro operaci čtení/zápisu, kde v jiných kontextech je jedna. K dispozici jsou důvody denormalizované čtení databáze, na které se můžete dozvědět v pokročilejší CQRS literatuře. Tento přístup ale nepoužíváme, protože cílem je mít větší flexibilitu v dotazech namísto omezení dotazů pomocí omezení ze DDD vzorů, jako jsou agregace.

Příkladem tohoto druhu služby je objednávání mikroslužby z referenční aplikace eShopOnContainers. Tato služba implementuje mikroslužby na základě zjednodušeného přístupu CQRS. Používá jeden zdroj dat nebo databázi, ale dva logické modely plus DDD vzory pro transakční doménu, jak je znázorněno na obrázku 7-2.

![Diagram znázorňující vysokou úroveň zjednodušené CQRS a DDD mikroslužby.](./media/apply-simplified-microservice-cqrs-ddd-patterns/simplified-cqrs-ddd-microservice.png)

**Obrázek 7-2**. Zjednodušená mikroslužba založená na CQRS a DDD

Logická služba "objednávání" zahrnuje databázi řazení, která může být, ale nemusí být stejným hostitelem Docker. Databáze ve stejném hostiteli Docker je dobrá pro vývoj, ale ne pro produkční prostředí.

Aplikační vrstva může být samotné webové rozhraní API. Důležitý aspekt návrhu je, že mikroslužba rozdělila dotazy a ViewModels (datové modely, zejména vytvořené pro klientské aplikace) z příkazů, doménového modelu a transakcí, které následují po vzoru CQRS. Tento přístup uchovává dotazy nezávislé na omezeních a omezeních, které pocházejí ze vzorů DDD, které dávají smysl jenom pro transakce a aktualizace, jak je vysvětleno v dalších částech.

## <a name="additional-resources"></a>Další zdroje informací:

- **Greg Young. Správa verzí v systému ve zdroji událostí** (bezplatné čtení elektronické knihy online) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Předchozí](index.md)@no__t – 1 –[Další](eshoponcontainers-cqrs-ddd-microservice.md)
