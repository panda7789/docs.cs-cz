---
title: Nativní interoperabilita – .NET
description: Zjistěte, jak spolupracovat s nativními komponentami v rozhraní .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 29aacc9210b4103f379b7776c36fc3c29b9e6dec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973555"
---
# <a name="native-interoperability"></a>Nativní interoperabilita

Následující články popisují různé způsoby provedení "nativní interoperabilita" v rozhraní .NET.

Existuje několik důvodů, proč byste to provádět volání do nativního kódu:

* Operační systémy jsou dostupné velký objem rozhraní API, která nejsou k dispozici v knihoven spravovaných tříd. Typickým příkladem pro tento scénář bude přístup k hardwaru nebo operačního systému funkce správy.
* Komunikace s ostatními součástmi, které máte, nebo můžete vytvořit instrukce ABI ve stylu jazyka C (nativní instrukce ABI), jako je například kód v Javě, který je zveřejněný prostřednictvím [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) nebo jiného spravovaného jazyka, který by mohla vést nativní součásti.
* Na Windows většina softwaru, který se nainstaluje, jako je například sada Microsoft Office, zaregistruje komponenty modelu COM, které představují své programy a vývojářům umožňuje automatizovat je nebo je používat. Tento proces také vyžaduje nativní interoperabilita.

Tento seznam nezahrnuje všechny potenciální situace a scénáře, ve kterých by vývojář chcete/typu/potřeba rozhraní s nativními komponentami. Knihovna tříd rozhraní .NET, například používá interoperabilitu nativní podporu k implementaci přiměřený počet jejích rozhraní API, jako je podpora konzoly a manipulaci s, přístupu k systému souborů a další. Je důležité si uvědomit, že je k dispozici možnost v případě potřeby.

> [!NOTE]
> Většina příkladů v této části se zobrazí pro všechny tři podporované platformy pro .NET Core (Windows, Linux a macOS). Ale příklady krátký a příkladů, stačí jeden vzorek je zobrazit, který používá rozšíření (to znamená "knihovny dll" pro knihovny) a názvy souborů Windows. To neznamená, že tyto funkce nejsou k dispozici v systému Linux nebo macOS, bylo provedeno pouze pro usnadnění práce saké.

## <a name="see-also"></a>Viz také:

- [Vyvolání platformy (nespravovaného)](pinvoke.md)
- [Zařazování typů](type-marshalling.md)
- [Osvědčené postupy nativní interoperabilita](best-practices.md)
