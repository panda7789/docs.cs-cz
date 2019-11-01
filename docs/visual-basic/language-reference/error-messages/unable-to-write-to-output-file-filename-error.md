---
title: "Nelze zapisovat do výstupního souboru '<filename>': <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 087735722fcd4dd789e25aacf6eeefffb490dac5
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198200"
---
# <a name="unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="968b7-102">Do výstupního souboru\<filename > se nedá zapisovat: Chyba \<</span><span class="sxs-lookup"><span data-stu-id="968b7-102">Unable to write to output file '\<filename>': \<error></span></span>
<span data-ttu-id="968b7-103">Při vytváření souboru došlo k potížím.</span><span class="sxs-lookup"><span data-stu-id="968b7-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="968b7-104">Výstupní soubor nelze otevřít pro zápis.</span><span class="sxs-lookup"><span data-stu-id="968b7-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="968b7-105">Soubor (nebo složku obsahující soubor) může být otevřen pro výhradní použití jiným procesem nebo může mít nastaven atribut jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="968b7-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="968b7-106">K běžným situacím, kdy se soubor otevírá výhradně, patří:</span><span class="sxs-lookup"><span data-stu-id="968b7-106">Common situations where a file is opened exclusively are:</span></span>  
  
- <span data-ttu-id="968b7-107">Aplikace už je spuštěná a používá její soubory.</span><span class="sxs-lookup"><span data-stu-id="968b7-107">The application is already running and using its files.</span></span> <span data-ttu-id="968b7-108">Chcete-li tento problém vyřešit, zajistěte, aby aplikace neběžela.</span><span class="sxs-lookup"><span data-stu-id="968b7-108">To solve this problem, make sure that the application is not running.</span></span>  
  
- <span data-ttu-id="968b7-109">Soubor otevřela jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="968b7-109">Another application has opened the file.</span></span> <span data-ttu-id="968b7-110">Chcete-li tento problém vyřešit, ujistěte se, že k souborům nepřistupuje žádná jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="968b7-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="968b7-111">Vždy není zřejmé, ke které aplikaci přistupuje vaše soubory; v takovém případě může být restartování počítače nejjednodušší způsob, jak aplikaci ukončit.</span><span class="sxs-lookup"><span data-stu-id="968b7-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="968b7-112">Pokud je i jeden z výstupních souborů projektu označen jen pro čtení, bude vyvolána tato výjimka.</span><span class="sxs-lookup"><span data-stu-id="968b7-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="968b7-113">**ID chyby:** BC31019</span><span class="sxs-lookup"><span data-stu-id="968b7-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="968b7-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="968b7-114">To correct this error</span></span>  
  
1. <span data-ttu-id="968b7-115">Zkompilujte program znovu, abyste viděli, jestli se chyba opakuje.</span><span class="sxs-lookup"><span data-stu-id="968b7-115">Compile the program again to see if the error recurs.</span></span>  
  
2. <span data-ttu-id="968b7-116">Pokud chyba přetrvává, uložte svou práci a restartujte aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="968b7-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3. <span data-ttu-id="968b7-117">Pokud chyba přetrvává, restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="968b7-117">If the error continues, restart the computer.</span></span>  
  
4. <span data-ttu-id="968b7-118">Pokud se chyba opakuje, přeinstalujte Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="968b7-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5. <span data-ttu-id="968b7-119">Pokud potíže potrvají i po přeinstalaci, upozorněte služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="968b7-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="968b7-120">Postup při kontrole atributů souborů v Průzkumníkovi souborů</span><span class="sxs-lookup"><span data-stu-id="968b7-120">To check file attributes in File Explorer</span></span>  
  
1. <span data-ttu-id="968b7-121">Otevřete složku, do které vás zajímáte.</span><span class="sxs-lookup"><span data-stu-id="968b7-121">Open the folder you are interested in.</span></span>  
  
2. <span data-ttu-id="968b7-122">Klikněte na ikonu **zobrazení** a vyberte **Podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="968b7-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3. <span data-ttu-id="968b7-123">Klikněte pravým tlačítkem myši na záhlaví sloupce a v rozevíracím seznamu vyberte možnost **atributy** .</span><span class="sxs-lookup"><span data-stu-id="968b7-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="968b7-124">Změna atributů souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="968b7-124">To change the attributes of a file or folder</span></span>  
  
1. <span data-ttu-id="968b7-125">V **Průzkumníku souborů**klikněte pravým tlačítkem na soubor nebo složku a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="968b7-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2. <span data-ttu-id="968b7-126">V části **atributy** na kartě **Obecné** zrušte zaškrtnutí políčka **jen pro čtení** .</span><span class="sxs-lookup"><span data-stu-id="968b7-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3. <span data-ttu-id="968b7-127">Stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="968b7-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968b7-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="968b7-128">See also</span></span>

- [<span data-ttu-id="968b7-129">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="968b7-129">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
