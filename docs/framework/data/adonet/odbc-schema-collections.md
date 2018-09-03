---
title: Kolekce schémat ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479977"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="7aa20-102">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="7aa20-102">ODBC Schema Collections</span></span>
<span data-ttu-id="7aa20-103">Tato část popisuje kolekci podpora schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="7aa20-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="7aa20-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="7aa20-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="7aa20-105">Ovladače ODBC Microsoft SQL Server podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="7aa20-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="7aa20-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="7aa20-106">Tables</span></span>  
  
-   <span data-ttu-id="7aa20-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="7aa20-107">Indexes</span></span>  
  
-   <span data-ttu-id="7aa20-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-108">Columns</span></span>  
  
-   <span data-ttu-id="7aa20-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="7aa20-109">Procedures</span></span>  
  
-   <span data-ttu-id="7aa20-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7aa20-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="7aa20-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7aa20-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="7aa20-112">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="7aa20-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="7aa20-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="7aa20-113">Tables and Views</span></span>  
  
|<span data-ttu-id="7aa20-114">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-114">ColumnName</span></span>|<span data-ttu-id="7aa20-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="7aa20-116">TABLE_CAT</span></span>|<span data-ttu-id="7aa20-117">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-117">String</span></span>|  
|<span data-ttu-id="7aa20-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7aa20-118">TABLE_SCHEM</span></span>|<span data-ttu-id="7aa20-119">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-119">String</span></span>|  
|<span data-ttu-id="7aa20-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-120">TABLE_NAME</span></span>|<span data-ttu-id="7aa20-121">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-121">String</span></span>|  
|<span data-ttu-id="7aa20-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-122">TABLE_TYPE</span></span>|<span data-ttu-id="7aa20-123">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-123">String</span></span>|  
|<span data-ttu-id="7aa20-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-124">REMARKS</span></span>|<span data-ttu-id="7aa20-125">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="7aa20-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="7aa20-126">Indexes</span></span>  
  
|<span data-ttu-id="7aa20-127">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-127">ColumnName</span></span>|<span data-ttu-id="7aa20-128">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="7aa20-129">TABLE_CAT</span></span>|<span data-ttu-id="7aa20-130">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-130">String</span></span>|  
|<span data-ttu-id="7aa20-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7aa20-131">TABLE_SCHEM</span></span>|<span data-ttu-id="7aa20-132">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-132">String</span></span>|  
|<span data-ttu-id="7aa20-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-133">TABLE_NAME</span></span>|<span data-ttu-id="7aa20-134">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-134">String</span></span>|  
|<span data-ttu-id="7aa20-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="7aa20-135">NON_UNIQUE</span></span>|<span data-ttu-id="7aa20-136">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-136">Int16</span></span>|  
|<span data-ttu-id="7aa20-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="7aa20-138">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-138">String</span></span>|  
|<span data-ttu-id="7aa20-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-139">INDEX_NAME</span></span>|<span data-ttu-id="7aa20-140">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-140">String</span></span>|  
|<span data-ttu-id="7aa20-141">TYP</span><span class="sxs-lookup"><span data-stu-id="7aa20-141">TYPE</span></span>|<span data-ttu-id="7aa20-142">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-142">Int16</span></span>|  
|<span data-ttu-id="7aa20-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-144">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-144">Int16</span></span>|  
|<span data-ttu-id="7aa20-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-145">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-146">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-146">String</span></span>|  
|<span data-ttu-id="7aa20-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="7aa20-147">ASC_OR_DESC</span></span>|<span data-ttu-id="7aa20-148">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-148">String</span></span>|  
|<span data-ttu-id="7aa20-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="7aa20-149">CARDINATLITY</span></span>|<span data-ttu-id="7aa20-150">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-150">Int32</span></span>|  
|<span data-ttu-id="7aa20-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-151">PAGES</span></span>|<span data-ttu-id="7aa20-152">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-152">Int32</span></span>|  
|<span data-ttu-id="7aa20-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-153">FILTER_CONDITION</span></span>|<span data-ttu-id="7aa20-154">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-154">String</span></span>|  
|<span data-ttu-id="7aa20-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7aa20-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="7aa20-156">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-156">String</span></span>|  
|<span data-ttu-id="7aa20-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="7aa20-158">Byte</span><span class="sxs-lookup"><span data-stu-id="7aa20-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="7aa20-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-159">Columns</span></span>  
  
|<span data-ttu-id="7aa20-160">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-160">ColumnName</span></span>|<span data-ttu-id="7aa20-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="7aa20-162">TABLE_CAT</span></span>|<span data-ttu-id="7aa20-163">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-163">String</span></span>|  
|<span data-ttu-id="7aa20-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7aa20-164">TABLE_SCHEM</span></span>|<span data-ttu-id="7aa20-165">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-165">String</span></span>|  
|<span data-ttu-id="7aa20-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-166">TABLE_NAME</span></span>|<span data-ttu-id="7aa20-167">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-167">String</span></span>|  
|<span data-ttu-id="7aa20-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-168">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-169">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-169">String</span></span>|  
|<span data-ttu-id="7aa20-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-170">DATA_TYPE</span></span>|<span data-ttu-id="7aa20-171">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-171">Int16</span></span>|  
|<span data-ttu-id="7aa20-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-172">TYPE_NAME</span></span>|<span data-ttu-id="7aa20-173">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-173">String</span></span>|  
|<span data-ttu-id="7aa20-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="7aa20-174">COLUMN_SIZE</span></span>|<span data-ttu-id="7aa20-175">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-175">Int32</span></span>|  
|<span data-ttu-id="7aa20-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7aa20-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="7aa20-177">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-177">Int32</span></span>|  
|<span data-ttu-id="7aa20-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="7aa20-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="7aa20-179">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-179">Int16</span></span>|  
|<span data-ttu-id="7aa20-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="7aa20-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="7aa20-181">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-181">Int16</span></span>|  
|<span data-ttu-id="7aa20-182">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="7aa20-182">NULLABLE</span></span>|<span data-ttu-id="7aa20-183">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-183">Int16</span></span>|  
|<span data-ttu-id="7aa20-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-184">REMARKS</span></span>|<span data-ttu-id="7aa20-185">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-185">String</span></span>|  
|<span data-ttu-id="7aa20-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="7aa20-186">COLUMN_DEF</span></span>|<span data-ttu-id="7aa20-187">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-187">String</span></span>|  
|<span data-ttu-id="7aa20-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="7aa20-189">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-189">Int16</span></span>|  
|<span data-ttu-id="7aa20-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="7aa20-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="7aa20-191">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-191">Int16</span></span>|  
|<span data-ttu-id="7aa20-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7aa20-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="7aa20-193">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-193">Int32</span></span>|  
|<span data-ttu-id="7aa20-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-195">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-195">Int32</span></span>|  
|<span data-ttu-id="7aa20-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7aa20-196">IS_NULLABLE</span></span>|<span data-ttu-id="7aa20-197">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-197">String</span></span>|  
|<span data-ttu-id="7aa20-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7aa20-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="7aa20-199">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-199">String</span></span>|  
|<span data-ttu-id="7aa20-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7aa20-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="7aa20-201">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-201">String</span></span>|  
|<span data-ttu-id="7aa20-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="7aa20-203">Byte</span><span class="sxs-lookup"><span data-stu-id="7aa20-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="7aa20-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="7aa20-204">Procedures</span></span>  
  
|<span data-ttu-id="7aa20-205">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-205">ColumnName</span></span>|<span data-ttu-id="7aa20-206">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="7aa20-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="7aa20-208">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-208">String</span></span>|  
|<span data-ttu-id="7aa20-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7aa20-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="7aa20-210">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-210">String</span></span>|  
|<span data-ttu-id="7aa20-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="7aa20-212">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-212">String</span></span>|  
|<span data-ttu-id="7aa20-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7aa20-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="7aa20-214">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-214">Int32</span></span>|  
|<span data-ttu-id="7aa20-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7aa20-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="7aa20-216">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-216">Int32</span></span>|  
|<span data-ttu-id="7aa20-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="7aa20-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="7aa20-218">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-218">Int32</span></span>|  
|<span data-ttu-id="7aa20-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-219">REMARKS</span></span>|<span data-ttu-id="7aa20-220">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-220">String</span></span>|  
|<span data-ttu-id="7aa20-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="7aa20-222">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="7aa20-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7aa20-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="7aa20-224">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-224">ColumnName</span></span>|<span data-ttu-id="7aa20-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="7aa20-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="7aa20-227">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-227">String</span></span>|  
|<span data-ttu-id="7aa20-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7aa20-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="7aa20-229">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-229">String</span></span>|  
|<span data-ttu-id="7aa20-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="7aa20-231">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-231">String</span></span>|  
|<span data-ttu-id="7aa20-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-232">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-233">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-233">String</span></span>|  
|<span data-ttu-id="7aa20-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-234">COLUMN_TYPE</span></span>|<span data-ttu-id="7aa20-235">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-235">Int16</span></span>|  
|<span data-ttu-id="7aa20-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-236">DATA_TYPE</span></span>|<span data-ttu-id="7aa20-237">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-237">Int16</span></span>|  
|<span data-ttu-id="7aa20-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-238">TYPE_NAME</span></span>|<span data-ttu-id="7aa20-239">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-239">String</span></span>|  
|<span data-ttu-id="7aa20-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="7aa20-240">COLUMN_SIZE</span></span>|<span data-ttu-id="7aa20-241">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-241">Int32</span></span>|  
|<span data-ttu-id="7aa20-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7aa20-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="7aa20-243">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-243">Int32</span></span>|  
|<span data-ttu-id="7aa20-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="7aa20-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="7aa20-245">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-245">Int16</span></span>|  
|<span data-ttu-id="7aa20-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="7aa20-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="7aa20-247">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-247">Int16</span></span>|  
|<span data-ttu-id="7aa20-248">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="7aa20-248">NULLABLE</span></span>|<span data-ttu-id="7aa20-249">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-249">Int16</span></span>|  
|<span data-ttu-id="7aa20-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-250">REMARKS</span></span>|<span data-ttu-id="7aa20-251">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-251">String</span></span>|  
|<span data-ttu-id="7aa20-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="7aa20-252">COLUMN_DEF</span></span>|<span data-ttu-id="7aa20-253">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-253">String</span></span>|  
|<span data-ttu-id="7aa20-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="7aa20-255">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-255">Int16</span></span>|  
|<span data-ttu-id="7aa20-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="7aa20-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="7aa20-257">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-257">Int16</span></span>|  
|<span data-ttu-id="7aa20-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7aa20-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="7aa20-259">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-259">Int32</span></span>|  
|<span data-ttu-id="7aa20-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-261">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-261">Int32</span></span>|  
|<span data-ttu-id="7aa20-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7aa20-262">IS_NULLABLE</span></span>|<span data-ttu-id="7aa20-263">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-263">String</span></span>|  
|<span data-ttu-id="7aa20-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7aa20-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="7aa20-265">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-265">String</span></span>|  
|<span data-ttu-id="7aa20-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7aa20-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="7aa20-267">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-267">String</span></span>|  
|<span data-ttu-id="7aa20-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="7aa20-269">Byte</span><span class="sxs-lookup"><span data-stu-id="7aa20-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="7aa20-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7aa20-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="7aa20-271">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-271">ColumnName</span></span>|<span data-ttu-id="7aa20-272">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="7aa20-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="7aa20-274">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-274">String</span></span>|  
|<span data-ttu-id="7aa20-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7aa20-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="7aa20-276">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-276">String</span></span>|  
|<span data-ttu-id="7aa20-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="7aa20-278">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-278">String</span></span>|  
|<span data-ttu-id="7aa20-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-279">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-280">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-280">String</span></span>|  
|<span data-ttu-id="7aa20-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-281">COLUMN_TYPE</span></span>|<span data-ttu-id="7aa20-282">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-282">Int16</span></span>|  
|<span data-ttu-id="7aa20-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-283">DATA_TYPE</span></span>|<span data-ttu-id="7aa20-284">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-284">Int16</span></span>|  
|<span data-ttu-id="7aa20-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-285">TYPE_NAME</span></span>|<span data-ttu-id="7aa20-286">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-286">String</span></span>|  
|<span data-ttu-id="7aa20-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="7aa20-287">COLUMN_SIZE</span></span>|<span data-ttu-id="7aa20-288">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-288">Int32</span></span>|  
|<span data-ttu-id="7aa20-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7aa20-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="7aa20-290">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-290">Int32</span></span>|  
|<span data-ttu-id="7aa20-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="7aa20-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="7aa20-292">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-292">Int16</span></span>|  
|<span data-ttu-id="7aa20-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="7aa20-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="7aa20-294">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-294">Int16</span></span>|  
|<span data-ttu-id="7aa20-295">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="7aa20-295">NULLABLE</span></span>|<span data-ttu-id="7aa20-296">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-296">Int16</span></span>|  
|<span data-ttu-id="7aa20-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-297">REMARKS</span></span>|<span data-ttu-id="7aa20-298">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-298">String</span></span>|  
|<span data-ttu-id="7aa20-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="7aa20-299">COLUMN_DEF</span></span>|<span data-ttu-id="7aa20-300">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-300">String</span></span>|  
|<span data-ttu-id="7aa20-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="7aa20-302">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-302">Int16</span></span>|  
|<span data-ttu-id="7aa20-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="7aa20-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="7aa20-304">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-304">Int16</span></span>|  
|<span data-ttu-id="7aa20-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7aa20-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="7aa20-306">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-306">Int32</span></span>|  
|<span data-ttu-id="7aa20-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-308">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-308">Int32</span></span>|  
|<span data-ttu-id="7aa20-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7aa20-309">IS_NULLABLE</span></span>|<span data-ttu-id="7aa20-310">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-310">String</span></span>|  
|<span data-ttu-id="7aa20-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7aa20-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="7aa20-312">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-312">String</span></span>|  
|<span data-ttu-id="7aa20-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7aa20-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="7aa20-314">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-314">String</span></span>|  
|<span data-ttu-id="7aa20-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="7aa20-316">Byte</span><span class="sxs-lookup"><span data-stu-id="7aa20-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="7aa20-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="7aa20-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="7aa20-318">Ovladače ODBC Microsoft SQL Server Oracle podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="7aa20-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="7aa20-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="7aa20-319">Tables</span></span>  
  
-   <span data-ttu-id="7aa20-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-320">Columns</span></span>  
  
-   <span data-ttu-id="7aa20-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="7aa20-321">Procedures</span></span>  
  
-   <span data-ttu-id="7aa20-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7aa20-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="7aa20-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7aa20-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="7aa20-324">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="7aa20-324">Views</span></span>  
  
-   <span data-ttu-id="7aa20-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="7aa20-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="7aa20-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="7aa20-326">Tables and Views</span></span>  
  
|<span data-ttu-id="7aa20-327">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-327">ColumnName</span></span>|<span data-ttu-id="7aa20-328">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="7aa20-330">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-330">String</span></span>|  
|<span data-ttu-id="7aa20-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7aa20-331">TABLE_OWNER</span></span>|<span data-ttu-id="7aa20-332">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-332">String</span></span>|  
|<span data-ttu-id="7aa20-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-333">TABLE_NAME</span></span>|<span data-ttu-id="7aa20-334">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-334">String</span></span>|  
|<span data-ttu-id="7aa20-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-335">TABLE_TYPE</span></span>|<span data-ttu-id="7aa20-336">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-336">String</span></span>|  
|<span data-ttu-id="7aa20-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-337">REMARKS</span></span>|<span data-ttu-id="7aa20-338">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="7aa20-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-339">Columns</span></span>  
  
|<span data-ttu-id="7aa20-340">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-340">ColumnName</span></span>|<span data-ttu-id="7aa20-341">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="7aa20-343">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-343">String</span></span>|  
|<span data-ttu-id="7aa20-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7aa20-344">TABLE_OWNER</span></span>|<span data-ttu-id="7aa20-345">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-345">String</span></span>|  
|<span data-ttu-id="7aa20-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-346">TABLE_NAME</span></span>|<span data-ttu-id="7aa20-347">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-347">String</span></span>|  
|<span data-ttu-id="7aa20-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-348">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-349">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-349">String</span></span>|  
|<span data-ttu-id="7aa20-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-350">DATA_TYPE</span></span>|<span data-ttu-id="7aa20-351">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-351">Int16</span></span>|  
|<span data-ttu-id="7aa20-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-352">TYPE_NAME</span></span>|<span data-ttu-id="7aa20-353">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-353">String</span></span>|  
|<span data-ttu-id="7aa20-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="7aa20-354">PRECISION</span></span>|<span data-ttu-id="7aa20-355">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-355">Int32</span></span>|  
|<span data-ttu-id="7aa20-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="7aa20-356">LENGTH</span></span>|<span data-ttu-id="7aa20-357">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-357">Int32</span></span>|  
|<span data-ttu-id="7aa20-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="7aa20-358">SCALE</span></span>|<span data-ttu-id="7aa20-359">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-359">Int16</span></span>|  
|<span data-ttu-id="7aa20-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="7aa20-360">RADIX</span></span>|<span data-ttu-id="7aa20-361">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-361">Int16</span></span>|  
|<span data-ttu-id="7aa20-362">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="7aa20-362">NULLABLE</span></span>|<span data-ttu-id="7aa20-363">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-363">Int16</span></span>|  
|<span data-ttu-id="7aa20-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-364">REMARKS</span></span>|<span data-ttu-id="7aa20-365">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-365">String</span></span>|  
|<span data-ttu-id="7aa20-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-367">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="7aa20-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="7aa20-368">Procedures</span></span>  
  
|<span data-ttu-id="7aa20-369">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-369">ColumnName</span></span>|<span data-ttu-id="7aa20-370">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="7aa20-372">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-372">String</span></span>|  
|<span data-ttu-id="7aa20-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7aa20-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="7aa20-374">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-374">String</span></span>|  
|<span data-ttu-id="7aa20-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="7aa20-376">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-376">String</span></span>|  
|<span data-ttu-id="7aa20-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7aa20-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="7aa20-378">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-378">Int16</span></span>|  
|<span data-ttu-id="7aa20-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7aa20-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="7aa20-380">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-380">Int16</span></span>|  
|<span data-ttu-id="7aa20-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="7aa20-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="7aa20-382">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-382">Int16</span></span>|  
|<span data-ttu-id="7aa20-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-383">REMARKS</span></span>|<span data-ttu-id="7aa20-384">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-384">String</span></span>|  
|<span data-ttu-id="7aa20-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="7aa20-386">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="7aa20-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7aa20-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="7aa20-388">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-388">ColumnName</span></span>|<span data-ttu-id="7aa20-389">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="7aa20-391">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-391">String</span></span>|  
|<span data-ttu-id="7aa20-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7aa20-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="7aa20-393">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-393">String</span></span>|  
|<span data-ttu-id="7aa20-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="7aa20-395">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-395">String</span></span>|  
|<span data-ttu-id="7aa20-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-396">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-397">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-397">String</span></span>|  
|<span data-ttu-id="7aa20-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-398">COLUMN_TYPE</span></span>|<span data-ttu-id="7aa20-399">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-399">Int16</span></span>|  
|<span data-ttu-id="7aa20-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-400">DATA_TYPE</span></span>|<span data-ttu-id="7aa20-401">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-401">Int16</span></span>|  
|<span data-ttu-id="7aa20-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-402">TYPE_NAME</span></span>|<span data-ttu-id="7aa20-403">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-403">String</span></span>|  
|<span data-ttu-id="7aa20-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="7aa20-404">PRECISION</span></span>|<span data-ttu-id="7aa20-405">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-405">Int32</span></span>|  
|<span data-ttu-id="7aa20-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="7aa20-406">LENGTH</span></span>|<span data-ttu-id="7aa20-407">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-407">Int32</span></span>|  
|<span data-ttu-id="7aa20-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="7aa20-408">SCALE</span></span>|<span data-ttu-id="7aa20-409">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-409">Int16</span></span>|  
|<span data-ttu-id="7aa20-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="7aa20-410">RADIX</span></span>|<span data-ttu-id="7aa20-411">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-411">Int16</span></span>|  
|<span data-ttu-id="7aa20-412">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="7aa20-412">NULLABLE</span></span>|<span data-ttu-id="7aa20-413">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-413">Int16</span></span>|  
|<span data-ttu-id="7aa20-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-414">REMARKS</span></span>|<span data-ttu-id="7aa20-415">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-415">String</span></span>|  
|<span data-ttu-id="7aa20-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="7aa20-416">OVERLOAD</span></span>|<span data-ttu-id="7aa20-417">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-417">Int32</span></span>|  
|<span data-ttu-id="7aa20-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-419">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="7aa20-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="7aa20-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="7aa20-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="7aa20-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="7aa20-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="7aa20-422">Tables</span></span>  
  
-   <span data-ttu-id="7aa20-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="7aa20-423">Indexes</span></span>  
  
-   <span data-ttu-id="7aa20-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-424">Columns</span></span>  
  
-   <span data-ttu-id="7aa20-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="7aa20-425">Procedures</span></span>  
  
-   <span data-ttu-id="7aa20-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7aa20-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="7aa20-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7aa20-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="7aa20-428">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="7aa20-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="7aa20-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="7aa20-429">Tables and Views</span></span>  
  
|<span data-ttu-id="7aa20-430">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-430">ColumnName</span></span>|<span data-ttu-id="7aa20-431">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="7aa20-433">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-433">String</span></span>|  
|<span data-ttu-id="7aa20-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7aa20-434">TABLE_OWNER</span></span>|<span data-ttu-id="7aa20-435">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-435">String</span></span>|  
|<span data-ttu-id="7aa20-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-436">TABLE_NAME</span></span>|<span data-ttu-id="7aa20-437">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-437">String</span></span>|  
|<span data-ttu-id="7aa20-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-438">TABLE_TYPE</span></span>|<span data-ttu-id="7aa20-439">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-439">String</span></span>|  
|<span data-ttu-id="7aa20-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-440">REMARKS</span></span>|<span data-ttu-id="7aa20-441">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="7aa20-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-442">Columns</span></span>  
  
|<span data-ttu-id="7aa20-443">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-443">ColumnName</span></span>|<span data-ttu-id="7aa20-444">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="7aa20-446">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-446">String</span></span>|  
|<span data-ttu-id="7aa20-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7aa20-447">TABLE_OWNER</span></span>|<span data-ttu-id="7aa20-448">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-448">String</span></span>|  
|<span data-ttu-id="7aa20-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-449">TABLE_NAME</span></span>|<span data-ttu-id="7aa20-450">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-450">String</span></span>|  
|<span data-ttu-id="7aa20-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-451">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-452">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-452">String</span></span>|  
|<span data-ttu-id="7aa20-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-453">DATA_TYPE</span></span>|<span data-ttu-id="7aa20-454">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-454">Int16</span></span>|  
|<span data-ttu-id="7aa20-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-455">TYPE_NAME</span></span>|<span data-ttu-id="7aa20-456">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-456">String</span></span>|  
|<span data-ttu-id="7aa20-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="7aa20-457">PRECISION</span></span>|<span data-ttu-id="7aa20-458">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-458">Int32</span></span>|  
|<span data-ttu-id="7aa20-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="7aa20-459">LENGTH</span></span>|<span data-ttu-id="7aa20-460">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-460">Int32</span></span>|  
|<span data-ttu-id="7aa20-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="7aa20-461">SCALE</span></span>|<span data-ttu-id="7aa20-462">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-462">Int16</span></span>|  
|<span data-ttu-id="7aa20-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="7aa20-463">RADIX</span></span>|<span data-ttu-id="7aa20-464">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-464">Int16</span></span>|  
|<span data-ttu-id="7aa20-465">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="7aa20-465">NULLABLE</span></span>|<span data-ttu-id="7aa20-466">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-466">Int16</span></span>|  
|<span data-ttu-id="7aa20-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-467">REMARKS</span></span>|<span data-ttu-id="7aa20-468">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-468">String</span></span>|  
|<span data-ttu-id="7aa20-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-470">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="7aa20-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="7aa20-471">Procedures</span></span>  
  
|<span data-ttu-id="7aa20-472">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-472">ColumnName</span></span>|<span data-ttu-id="7aa20-473">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="7aa20-475">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-475">String</span></span>|  
|<span data-ttu-id="7aa20-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7aa20-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="7aa20-477">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-477">String</span></span>|  
|<span data-ttu-id="7aa20-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="7aa20-479">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-479">String</span></span>|  
|<span data-ttu-id="7aa20-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7aa20-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="7aa20-481">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-481">Int16</span></span>|  
|<span data-ttu-id="7aa20-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7aa20-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="7aa20-483">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-483">Int16</span></span>|  
|<span data-ttu-id="7aa20-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="7aa20-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="7aa20-485">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-485">Int16</span></span>|  
|<span data-ttu-id="7aa20-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-486">REMARKS</span></span>|<span data-ttu-id="7aa20-487">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-487">String</span></span>|  
|<span data-ttu-id="7aa20-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="7aa20-489">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="7aa20-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7aa20-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="7aa20-491">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-491">ColumnName</span></span>|<span data-ttu-id="7aa20-492">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7aa20-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="7aa20-494">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-494">String</span></span>|  
|<span data-ttu-id="7aa20-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7aa20-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="7aa20-496">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-496">String</span></span>|  
|<span data-ttu-id="7aa20-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="7aa20-498">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-498">String</span></span>|  
|<span data-ttu-id="7aa20-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-499">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-500">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-500">String</span></span>|  
|<span data-ttu-id="7aa20-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-501">COLUMN_TYPE</span></span>|<span data-ttu-id="7aa20-502">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-502">Int16</span></span>|  
|<span data-ttu-id="7aa20-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-503">DATA_TYPE</span></span>|<span data-ttu-id="7aa20-504">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-504">Int16</span></span>|  
|<span data-ttu-id="7aa20-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-505">TYPE_NAME</span></span>|<span data-ttu-id="7aa20-506">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-506">String</span></span>|  
|<span data-ttu-id="7aa20-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="7aa20-507">PRECISION</span></span>|<span data-ttu-id="7aa20-508">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-508">Int32</span></span>|  
|<span data-ttu-id="7aa20-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="7aa20-509">LENGTH</span></span>|<span data-ttu-id="7aa20-510">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-510">Int32</span></span>|  
|<span data-ttu-id="7aa20-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="7aa20-511">SCALE</span></span>|<span data-ttu-id="7aa20-512">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-512">Int16</span></span>|  
|<span data-ttu-id="7aa20-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="7aa20-513">RADIX</span></span>|<span data-ttu-id="7aa20-514">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-514">Int16</span></span>|  
|<span data-ttu-id="7aa20-515">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="7aa20-515">NULLABLE</span></span>|<span data-ttu-id="7aa20-516">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-516">Int16</span></span>|  
|<span data-ttu-id="7aa20-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-517">REMARKS</span></span>|<span data-ttu-id="7aa20-518">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-518">String</span></span>|  
|<span data-ttu-id="7aa20-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="7aa20-519">OVERLOAD</span></span>|<span data-ttu-id="7aa20-520">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-520">Int32</span></span>|  
|<span data-ttu-id="7aa20-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-522">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="7aa20-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7aa20-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="7aa20-524">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="7aa20-524">ColumnName</span></span>|<span data-ttu-id="7aa20-525">Datový typ</span><span class="sxs-lookup"><span data-stu-id="7aa20-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7aa20-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="7aa20-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="7aa20-527">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-527">String</span></span>|  
|<span data-ttu-id="7aa20-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7aa20-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="7aa20-529">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-529">String</span></span>|  
|<span data-ttu-id="7aa20-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="7aa20-531">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-531">String</span></span>|  
|<span data-ttu-id="7aa20-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-532">COLUMN_NAME</span></span>|<span data-ttu-id="7aa20-533">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-533">String</span></span>|  
|<span data-ttu-id="7aa20-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-534">COLUMN_TYPE</span></span>|<span data-ttu-id="7aa20-535">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-535">Int16</span></span>|  
|<span data-ttu-id="7aa20-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-536">DATA_TYPE</span></span>|<span data-ttu-id="7aa20-537">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-537">Int16</span></span>|  
|<span data-ttu-id="7aa20-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7aa20-538">TYPE_NAME</span></span>|<span data-ttu-id="7aa20-539">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-539">String</span></span>|  
|<span data-ttu-id="7aa20-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="7aa20-540">COLUMN_SIZE</span></span>|<span data-ttu-id="7aa20-541">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-541">Int32</span></span>|  
|<span data-ttu-id="7aa20-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7aa20-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="7aa20-543">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-543">Int32</span></span>|  
|<span data-ttu-id="7aa20-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="7aa20-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="7aa20-545">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-545">Int16</span></span>|  
|<span data-ttu-id="7aa20-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="7aa20-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="7aa20-547">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-547">Int16</span></span>|  
|<span data-ttu-id="7aa20-548">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="7aa20-548">NULLABLE</span></span>|<span data-ttu-id="7aa20-549">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-549">Int16</span></span>|  
|<span data-ttu-id="7aa20-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="7aa20-550">REMARKS</span></span>|<span data-ttu-id="7aa20-551">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-551">String</span></span>|  
|<span data-ttu-id="7aa20-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="7aa20-552">COLUMN_DEF</span></span>|<span data-ttu-id="7aa20-553">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-553">String</span></span>|  
|<span data-ttu-id="7aa20-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7aa20-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="7aa20-555">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-555">Int16</span></span>|  
|<span data-ttu-id="7aa20-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="7aa20-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="7aa20-557">Int16</span><span class="sxs-lookup"><span data-stu-id="7aa20-557">Int16</span></span>|  
|<span data-ttu-id="7aa20-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7aa20-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="7aa20-559">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-559">Int32</span></span>|  
|<span data-ttu-id="7aa20-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7aa20-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="7aa20-561">Int32</span><span class="sxs-lookup"><span data-stu-id="7aa20-561">Int32</span></span>|  
|<span data-ttu-id="7aa20-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7aa20-562">IS_NULLABLE</span></span>|<span data-ttu-id="7aa20-563">String</span><span class="sxs-lookup"><span data-stu-id="7aa20-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7aa20-564">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aa20-564">See Also</span></span>  
 [<span data-ttu-id="7aa20-565">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7aa20-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
