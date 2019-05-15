---
title: 'Postupy: Opakované přehrávání zvuku ve formuláři Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: e14d9de2326234b86c1f24b227e86f822fbfdb71
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592356"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>Postupy: Opakované přehrávání zvuku ve formuláři Windows Forms
Následující příklad kódu opakovaně přehraje zvuk. Když kód v `stopPlayingButton_Click` spustí obslužnou rutinu události, všechny aktuálně přehrávání zastaví zvuku. Pokud žádný zvukový signál přehrávání, nic se nestane.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému a System.Windows.Forms.  
  
- Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platným názvem souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Operace se soubory by měl být uzavřen v rámci příslušné zpracování výjimek bloků.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název cesty je poškozený. Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException> třídy).  
  
- Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).  
  
- Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).  
  
- Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).  
  
- Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).  
  
- Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic. Před použitím dat ve své aplikaci ověřte všechny vstupy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [Postupy: Přehrávání zvuku z formuláře Windows](how-to-play-a-sound-from-a-windows-form.md)
- [Přehled třídy SoundPlayer](soundplayer-class-overview.md)
