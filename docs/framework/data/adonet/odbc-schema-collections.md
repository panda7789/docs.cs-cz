---
title: Kolekce schémat ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772044"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="8a8bd-102">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="8a8bd-102">ODBC Schema Collections</span></span>

<span data-ttu-id="8a8bd-103">Tato část popisuje kolekci podpora schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="8a8bd-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="8a8bd-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="8a8bd-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="8a8bd-105">Ovladače ODBC Microsoft SQL Server podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="8a8bd-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="8a8bd-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="8a8bd-106">Tables</span></span>

- <span data-ttu-id="8a8bd-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="8a8bd-107">Indexes</span></span>

- <span data-ttu-id="8a8bd-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-108">Columns</span></span>

- <span data-ttu-id="8a8bd-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="8a8bd-109">Procedures</span></span>

- <span data-ttu-id="8a8bd-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8a8bd-110">ProcedureColumns</span></span>

- <span data-ttu-id="8a8bd-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8a8bd-111">ProcedureParameters</span></span>

- <span data-ttu-id="8a8bd-112">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="8a8bd-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="8a8bd-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="8a8bd-113">Tables and Views</span></span>

|<span data-ttu-id="8a8bd-114">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-114">ColumnName</span></span>|<span data-ttu-id="8a8bd-115">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="8a8bd-116">TABLE_CAT</span></span>|<span data-ttu-id="8a8bd-117">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-117">String</span></span>|
|<span data-ttu-id="8a8bd-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="8a8bd-118">TABLE_SCHEM</span></span>|<span data-ttu-id="8a8bd-119">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-119">String</span></span>|
|<span data-ttu-id="8a8bd-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-120">TABLE_NAME</span></span>|<span data-ttu-id="8a8bd-121">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-121">String</span></span>|
|<span data-ttu-id="8a8bd-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-122">TABLE_TYPE</span></span>|<span data-ttu-id="8a8bd-123">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-123">String</span></span>|
|<span data-ttu-id="8a8bd-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-124">REMARKS</span></span>|<span data-ttu-id="8a8bd-125">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="8a8bd-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="8a8bd-126">Indexes</span></span>

|<span data-ttu-id="8a8bd-127">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-127">ColumnName</span></span>|<span data-ttu-id="8a8bd-128">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="8a8bd-129">TABLE_CAT</span></span>|<span data-ttu-id="8a8bd-130">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-130">String</span></span>|
|<span data-ttu-id="8a8bd-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="8a8bd-131">TABLE_SCHEM</span></span>|<span data-ttu-id="8a8bd-132">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-132">String</span></span>|
|<span data-ttu-id="8a8bd-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-133">TABLE_NAME</span></span>|<span data-ttu-id="8a8bd-134">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-134">String</span></span>|
|<span data-ttu-id="8a8bd-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-135">NON_UNIQUE</span></span>|<span data-ttu-id="8a8bd-136">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-136">Int16</span></span>|
|<span data-ttu-id="8a8bd-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-138">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-138">String</span></span>|
|<span data-ttu-id="8a8bd-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-139">INDEX_NAME</span></span>|<span data-ttu-id="8a8bd-140">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-140">String</span></span>|
|<span data-ttu-id="8a8bd-141">TYP</span><span class="sxs-lookup"><span data-stu-id="8a8bd-141">TYPE</span></span>|<span data-ttu-id="8a8bd-142">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-142">Int16</span></span>|
|<span data-ttu-id="8a8bd-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-144">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-144">Int16</span></span>|
|<span data-ttu-id="8a8bd-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-145">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-146">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-146">String</span></span>|
|<span data-ttu-id="8a8bd-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="8a8bd-147">ASC_OR_DESC</span></span>|<span data-ttu-id="8a8bd-148">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-148">String</span></span>|
|<span data-ttu-id="8a8bd-149">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-149">CARDINALITY</span></span>|<span data-ttu-id="8a8bd-150">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-150">Int32</span></span>|
|<span data-ttu-id="8a8bd-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-151">PAGES</span></span>|<span data-ttu-id="8a8bd-152">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-152">Int32</span></span>|
|<span data-ttu-id="8a8bd-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-153">FILTER_CONDITION</span></span>|<span data-ttu-id="8a8bd-154">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-154">String</span></span>|
|<span data-ttu-id="8a8bd-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="8a8bd-156">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-156">String</span></span>|
|<span data-ttu-id="8a8bd-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-158">Byte</span><span class="sxs-lookup"><span data-stu-id="8a8bd-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="8a8bd-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-159">Columns</span></span>

|<span data-ttu-id="8a8bd-160">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-160">ColumnName</span></span>|<span data-ttu-id="8a8bd-161">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="8a8bd-162">TABLE_CAT</span></span>|<span data-ttu-id="8a8bd-163">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-163">String</span></span>|
|<span data-ttu-id="8a8bd-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="8a8bd-164">TABLE_SCHEM</span></span>|<span data-ttu-id="8a8bd-165">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-165">String</span></span>|
|<span data-ttu-id="8a8bd-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-166">TABLE_NAME</span></span>|<span data-ttu-id="8a8bd-167">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-167">String</span></span>|
|<span data-ttu-id="8a8bd-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-168">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-169">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-169">String</span></span>|
|<span data-ttu-id="8a8bd-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-170">DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-171">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-171">Int16</span></span>|
|<span data-ttu-id="8a8bd-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-172">TYPE_NAME</span></span>|<span data-ttu-id="8a8bd-173">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-173">String</span></span>|
|<span data-ttu-id="8a8bd-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-174">COLUMN_SIZE</span></span>|<span data-ttu-id="8a8bd-175">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-175">Int32</span></span>|
|<span data-ttu-id="8a8bd-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8a8bd-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="8a8bd-177">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-177">Int32</span></span>|
|<span data-ttu-id="8a8bd-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="8a8bd-179">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-179">Int16</span></span>|
|<span data-ttu-id="8a8bd-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="8a8bd-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="8a8bd-181">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-181">Int16</span></span>|
|<span data-ttu-id="8a8bd-182">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="8a8bd-182">NULLABLE</span></span>|<span data-ttu-id="8a8bd-183">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-183">Int16</span></span>|
|<span data-ttu-id="8a8bd-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-184">REMARKS</span></span>|<span data-ttu-id="8a8bd-185">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-185">String</span></span>|
|<span data-ttu-id="8a8bd-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="8a8bd-186">COLUMN_DEF</span></span>|<span data-ttu-id="8a8bd-187">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-187">String</span></span>|
|<span data-ttu-id="8a8bd-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-189">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-189">Int16</span></span>|
|<span data-ttu-id="8a8bd-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="8a8bd-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="8a8bd-191">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-191">Int16</span></span>|
|<span data-ttu-id="8a8bd-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8a8bd-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="8a8bd-193">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-193">Int32</span></span>|
|<span data-ttu-id="8a8bd-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-195">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-195">Int32</span></span>|
|<span data-ttu-id="8a8bd-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-196">IS_NULLABLE</span></span>|<span data-ttu-id="8a8bd-197">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-197">String</span></span>|
|<span data-ttu-id="8a8bd-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8a8bd-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="8a8bd-199">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-199">String</span></span>|
|<span data-ttu-id="8a8bd-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="8a8bd-201">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-201">String</span></span>|
|<span data-ttu-id="8a8bd-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-203">Byte</span><span class="sxs-lookup"><span data-stu-id="8a8bd-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="8a8bd-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="8a8bd-204">Procedures</span></span>

|<span data-ttu-id="8a8bd-205">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-205">ColumnName</span></span>|<span data-ttu-id="8a8bd-206">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="8a8bd-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="8a8bd-208">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-208">String</span></span>|
|<span data-ttu-id="8a8bd-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="8a8bd-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="8a8bd-210">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-210">String</span></span>|
|<span data-ttu-id="8a8bd-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="8a8bd-212">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-212">String</span></span>|
|<span data-ttu-id="8a8bd-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="8a8bd-214">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-214">Int32</span></span>|
|<span data-ttu-id="8a8bd-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="8a8bd-216">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-216">Int32</span></span>|
|<span data-ttu-id="8a8bd-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="8a8bd-218">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-218">Int32</span></span>|
|<span data-ttu-id="8a8bd-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-219">REMARKS</span></span>|<span data-ttu-id="8a8bd-220">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-220">String</span></span>|
|<span data-ttu-id="8a8bd-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8a8bd-222">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="8a8bd-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8a8bd-223">ProcedureColumns</span></span>

|<span data-ttu-id="8a8bd-224">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-224">ColumnName</span></span>|<span data-ttu-id="8a8bd-225">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="8a8bd-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="8a8bd-227">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-227">String</span></span>|
|<span data-ttu-id="8a8bd-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="8a8bd-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="8a8bd-229">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-229">String</span></span>|
|<span data-ttu-id="8a8bd-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="8a8bd-231">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-231">String</span></span>|
|<span data-ttu-id="8a8bd-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-232">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-233">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-233">String</span></span>|
|<span data-ttu-id="8a8bd-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-234">COLUMN_TYPE</span></span>|<span data-ttu-id="8a8bd-235">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-235">Int16</span></span>|
|<span data-ttu-id="8a8bd-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-236">DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-237">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-237">Int16</span></span>|
|<span data-ttu-id="8a8bd-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-238">TYPE_NAME</span></span>|<span data-ttu-id="8a8bd-239">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-239">String</span></span>|
|<span data-ttu-id="8a8bd-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-240">COLUMN_SIZE</span></span>|<span data-ttu-id="8a8bd-241">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-241">Int32</span></span>|
|<span data-ttu-id="8a8bd-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8a8bd-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="8a8bd-243">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-243">Int32</span></span>|
|<span data-ttu-id="8a8bd-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="8a8bd-245">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-245">Int16</span></span>|
|<span data-ttu-id="8a8bd-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="8a8bd-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="8a8bd-247">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-247">Int16</span></span>|
|<span data-ttu-id="8a8bd-248">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="8a8bd-248">NULLABLE</span></span>|<span data-ttu-id="8a8bd-249">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-249">Int16</span></span>|
|<span data-ttu-id="8a8bd-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-250">REMARKS</span></span>|<span data-ttu-id="8a8bd-251">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-251">String</span></span>|
|<span data-ttu-id="8a8bd-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="8a8bd-252">COLUMN_DEF</span></span>|<span data-ttu-id="8a8bd-253">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-253">String</span></span>|
|<span data-ttu-id="8a8bd-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-255">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-255">Int16</span></span>|
|<span data-ttu-id="8a8bd-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="8a8bd-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="8a8bd-257">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-257">Int16</span></span>|
|<span data-ttu-id="8a8bd-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8a8bd-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="8a8bd-259">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-259">Int32</span></span>|
|<span data-ttu-id="8a8bd-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-261">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-261">Int32</span></span>|
|<span data-ttu-id="8a8bd-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-262">IS_NULLABLE</span></span>|<span data-ttu-id="8a8bd-263">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-263">String</span></span>|
|<span data-ttu-id="8a8bd-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8a8bd-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="8a8bd-265">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-265">String</span></span>|
|<span data-ttu-id="8a8bd-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="8a8bd-267">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-267">String</span></span>|
|<span data-ttu-id="8a8bd-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-269">Byte</span><span class="sxs-lookup"><span data-stu-id="8a8bd-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="8a8bd-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8a8bd-270">ProcedureParameters</span></span>

|<span data-ttu-id="8a8bd-271">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-271">ColumnName</span></span>|<span data-ttu-id="8a8bd-272">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="8a8bd-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="8a8bd-274">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-274">String</span></span>|
|<span data-ttu-id="8a8bd-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="8a8bd-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="8a8bd-276">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-276">String</span></span>|
|<span data-ttu-id="8a8bd-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="8a8bd-278">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-278">String</span></span>|
|<span data-ttu-id="8a8bd-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-279">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-280">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-280">String</span></span>|
|<span data-ttu-id="8a8bd-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-281">COLUMN_TYPE</span></span>|<span data-ttu-id="8a8bd-282">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-282">Int16</span></span>|
|<span data-ttu-id="8a8bd-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-283">DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-284">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-284">Int16</span></span>|
|<span data-ttu-id="8a8bd-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-285">TYPE_NAME</span></span>|<span data-ttu-id="8a8bd-286">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-286">String</span></span>|
|<span data-ttu-id="8a8bd-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-287">COLUMN_SIZE</span></span>|<span data-ttu-id="8a8bd-288">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-288">Int32</span></span>|
|<span data-ttu-id="8a8bd-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8a8bd-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="8a8bd-290">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-290">Int32</span></span>|
|<span data-ttu-id="8a8bd-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="8a8bd-292">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-292">Int16</span></span>|
|<span data-ttu-id="8a8bd-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="8a8bd-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="8a8bd-294">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-294">Int16</span></span>|
|<span data-ttu-id="8a8bd-295">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="8a8bd-295">NULLABLE</span></span>|<span data-ttu-id="8a8bd-296">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-296">Int16</span></span>|
|<span data-ttu-id="8a8bd-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-297">REMARKS</span></span>|<span data-ttu-id="8a8bd-298">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-298">String</span></span>|
|<span data-ttu-id="8a8bd-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="8a8bd-299">COLUMN_DEF</span></span>|<span data-ttu-id="8a8bd-300">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-300">String</span></span>|
|<span data-ttu-id="8a8bd-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-302">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-302">Int16</span></span>|
|<span data-ttu-id="8a8bd-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="8a8bd-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="8a8bd-304">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-304">Int16</span></span>|
|<span data-ttu-id="8a8bd-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8a8bd-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="8a8bd-306">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-306">Int32</span></span>|
|<span data-ttu-id="8a8bd-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-308">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-308">Int32</span></span>|
|<span data-ttu-id="8a8bd-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-309">IS_NULLABLE</span></span>|<span data-ttu-id="8a8bd-310">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-310">String</span></span>|
|<span data-ttu-id="8a8bd-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8a8bd-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="8a8bd-312">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-312">String</span></span>|
|<span data-ttu-id="8a8bd-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="8a8bd-314">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-314">String</span></span>|
|<span data-ttu-id="8a8bd-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-316">Byte</span><span class="sxs-lookup"><span data-stu-id="8a8bd-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="8a8bd-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="8a8bd-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="8a8bd-318">Ovladače ODBC Microsoft SQL Server Oracle podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="8a8bd-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="8a8bd-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="8a8bd-319">Tables</span></span>

- <span data-ttu-id="8a8bd-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-320">Columns</span></span>

- <span data-ttu-id="8a8bd-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="8a8bd-321">Procedures</span></span>

- <span data-ttu-id="8a8bd-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8a8bd-322">ProcedureColumns</span></span>

- <span data-ttu-id="8a8bd-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8a8bd-323">ProcedureParameters</span></span>

- <span data-ttu-id="8a8bd-324">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="8a8bd-324">Views</span></span>

- <span data-ttu-id="8a8bd-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="8a8bd-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="8a8bd-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="8a8bd-326">Tables and Views</span></span>

|<span data-ttu-id="8a8bd-327">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-327">ColumnName</span></span>|<span data-ttu-id="8a8bd-328">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-330">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-330">String</span></span>|
|<span data-ttu-id="8a8bd-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-331">TABLE_OWNER</span></span>|<span data-ttu-id="8a8bd-332">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-332">String</span></span>|
|<span data-ttu-id="8a8bd-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-333">TABLE_NAME</span></span>|<span data-ttu-id="8a8bd-334">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-334">String</span></span>|
|<span data-ttu-id="8a8bd-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-335">TABLE_TYPE</span></span>|<span data-ttu-id="8a8bd-336">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-336">String</span></span>|
|<span data-ttu-id="8a8bd-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-337">REMARKS</span></span>|<span data-ttu-id="8a8bd-338">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="8a8bd-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-339">Columns</span></span>

|<span data-ttu-id="8a8bd-340">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-340">ColumnName</span></span>|<span data-ttu-id="8a8bd-341">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-343">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-343">String</span></span>|
|<span data-ttu-id="8a8bd-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-344">TABLE_OWNER</span></span>|<span data-ttu-id="8a8bd-345">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-345">String</span></span>|
|<span data-ttu-id="8a8bd-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-346">TABLE_NAME</span></span>|<span data-ttu-id="8a8bd-347">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-347">String</span></span>|
|<span data-ttu-id="8a8bd-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-348">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-349">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-349">String</span></span>|
|<span data-ttu-id="8a8bd-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-350">DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-351">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-351">Int16</span></span>|
|<span data-ttu-id="8a8bd-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-352">TYPE_NAME</span></span>|<span data-ttu-id="8a8bd-353">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-353">String</span></span>|
|<span data-ttu-id="8a8bd-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="8a8bd-354">PRECISION</span></span>|<span data-ttu-id="8a8bd-355">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-355">Int32</span></span>|
|<span data-ttu-id="8a8bd-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-356">LENGTH</span></span>|<span data-ttu-id="8a8bd-357">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-357">Int32</span></span>|
|<span data-ttu-id="8a8bd-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="8a8bd-358">SCALE</span></span>|<span data-ttu-id="8a8bd-359">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-359">Int16</span></span>|
|<span data-ttu-id="8a8bd-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="8a8bd-360">RADIX</span></span>|<span data-ttu-id="8a8bd-361">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-361">Int16</span></span>|
|<span data-ttu-id="8a8bd-362">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="8a8bd-362">NULLABLE</span></span>|<span data-ttu-id="8a8bd-363">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-363">Int16</span></span>|
|<span data-ttu-id="8a8bd-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-364">REMARKS</span></span>|<span data-ttu-id="8a8bd-365">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-365">String</span></span>|
|<span data-ttu-id="8a8bd-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-367">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="8a8bd-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="8a8bd-368">Procedures</span></span>

|<span data-ttu-id="8a8bd-369">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-369">ColumnName</span></span>|<span data-ttu-id="8a8bd-370">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-372">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-372">String</span></span>|
|<span data-ttu-id="8a8bd-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="8a8bd-374">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-374">String</span></span>|
|<span data-ttu-id="8a8bd-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="8a8bd-376">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-376">String</span></span>|
|<span data-ttu-id="8a8bd-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="8a8bd-378">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-378">Int16</span></span>|
|<span data-ttu-id="8a8bd-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="8a8bd-380">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-380">Int16</span></span>|
|<span data-ttu-id="8a8bd-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="8a8bd-382">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-382">Int16</span></span>|
|<span data-ttu-id="8a8bd-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-383">REMARKS</span></span>|<span data-ttu-id="8a8bd-384">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-384">String</span></span>|
|<span data-ttu-id="8a8bd-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8a8bd-386">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="8a8bd-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8a8bd-387">ProcedureColumns</span></span>

|<span data-ttu-id="8a8bd-388">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-388">ColumnName</span></span>|<span data-ttu-id="8a8bd-389">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-391">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-391">String</span></span>|
|<span data-ttu-id="8a8bd-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="8a8bd-393">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-393">String</span></span>|
|<span data-ttu-id="8a8bd-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="8a8bd-395">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-395">String</span></span>|
|<span data-ttu-id="8a8bd-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-396">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-397">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-397">String</span></span>|
|<span data-ttu-id="8a8bd-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-398">COLUMN_TYPE</span></span>|<span data-ttu-id="8a8bd-399">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-399">Int16</span></span>|
|<span data-ttu-id="8a8bd-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-400">DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-401">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-401">Int16</span></span>|
|<span data-ttu-id="8a8bd-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-402">TYPE_NAME</span></span>|<span data-ttu-id="8a8bd-403">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-403">String</span></span>|
|<span data-ttu-id="8a8bd-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="8a8bd-404">PRECISION</span></span>|<span data-ttu-id="8a8bd-405">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-405">Int32</span></span>|
|<span data-ttu-id="8a8bd-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-406">LENGTH</span></span>|<span data-ttu-id="8a8bd-407">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-407">Int32</span></span>|
|<span data-ttu-id="8a8bd-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="8a8bd-408">SCALE</span></span>|<span data-ttu-id="8a8bd-409">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-409">Int16</span></span>|
|<span data-ttu-id="8a8bd-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="8a8bd-410">RADIX</span></span>|<span data-ttu-id="8a8bd-411">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-411">Int16</span></span>|
|<span data-ttu-id="8a8bd-412">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="8a8bd-412">NULLABLE</span></span>|<span data-ttu-id="8a8bd-413">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-413">Int16</span></span>|
|<span data-ttu-id="8a8bd-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-414">REMARKS</span></span>|<span data-ttu-id="8a8bd-415">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-415">String</span></span>|
|<span data-ttu-id="8a8bd-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="8a8bd-416">OVERLOAD</span></span>|<span data-ttu-id="8a8bd-417">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-417">Int32</span></span>|
|<span data-ttu-id="8a8bd-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-419">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="8a8bd-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="8a8bd-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="8a8bd-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="8a8bd-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="8a8bd-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="8a8bd-422">Tables</span></span>

- <span data-ttu-id="8a8bd-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="8a8bd-423">Indexes</span></span>

- <span data-ttu-id="8a8bd-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-424">Columns</span></span>

- <span data-ttu-id="8a8bd-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="8a8bd-425">Procedures</span></span>

- <span data-ttu-id="8a8bd-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8a8bd-426">ProcedureColumns</span></span>

- <span data-ttu-id="8a8bd-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8a8bd-427">ProcedureParameters</span></span>

- <span data-ttu-id="8a8bd-428">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="8a8bd-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="8a8bd-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="8a8bd-429">Tables and Views</span></span>

|<span data-ttu-id="8a8bd-430">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-430">ColumnName</span></span>|<span data-ttu-id="8a8bd-431">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-433">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-433">String</span></span>|
|<span data-ttu-id="8a8bd-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-434">TABLE_OWNER</span></span>|<span data-ttu-id="8a8bd-435">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-435">String</span></span>|
|<span data-ttu-id="8a8bd-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-436">TABLE_NAME</span></span>|<span data-ttu-id="8a8bd-437">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-437">String</span></span>|
|<span data-ttu-id="8a8bd-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-438">TABLE_TYPE</span></span>|<span data-ttu-id="8a8bd-439">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-439">String</span></span>|
|<span data-ttu-id="8a8bd-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-440">REMARKS</span></span>|<span data-ttu-id="8a8bd-441">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="8a8bd-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-442">Columns</span></span>

|<span data-ttu-id="8a8bd-443">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-443">ColumnName</span></span>|<span data-ttu-id="8a8bd-444">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-446">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-446">String</span></span>|
|<span data-ttu-id="8a8bd-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-447">TABLE_OWNER</span></span>|<span data-ttu-id="8a8bd-448">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-448">String</span></span>|
|<span data-ttu-id="8a8bd-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-449">TABLE_NAME</span></span>|<span data-ttu-id="8a8bd-450">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-450">String</span></span>|
|<span data-ttu-id="8a8bd-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-451">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-452">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-452">String</span></span>|
|<span data-ttu-id="8a8bd-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-453">DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-454">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-454">Int16</span></span>|
|<span data-ttu-id="8a8bd-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-455">TYPE_NAME</span></span>|<span data-ttu-id="8a8bd-456">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-456">String</span></span>|
|<span data-ttu-id="8a8bd-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="8a8bd-457">PRECISION</span></span>|<span data-ttu-id="8a8bd-458">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-458">Int32</span></span>|
|<span data-ttu-id="8a8bd-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-459">LENGTH</span></span>|<span data-ttu-id="8a8bd-460">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-460">Int32</span></span>|
|<span data-ttu-id="8a8bd-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="8a8bd-461">SCALE</span></span>|<span data-ttu-id="8a8bd-462">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-462">Int16</span></span>|
|<span data-ttu-id="8a8bd-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="8a8bd-463">RADIX</span></span>|<span data-ttu-id="8a8bd-464">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-464">Int16</span></span>|
|<span data-ttu-id="8a8bd-465">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="8a8bd-465">NULLABLE</span></span>|<span data-ttu-id="8a8bd-466">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-466">Int16</span></span>|
|<span data-ttu-id="8a8bd-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-467">REMARKS</span></span>|<span data-ttu-id="8a8bd-468">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-468">String</span></span>|
|<span data-ttu-id="8a8bd-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-470">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="8a8bd-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="8a8bd-471">Procedures</span></span>

|<span data-ttu-id="8a8bd-472">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-472">ColumnName</span></span>|<span data-ttu-id="8a8bd-473">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-475">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-475">String</span></span>|
|<span data-ttu-id="8a8bd-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="8a8bd-477">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-477">String</span></span>|
|<span data-ttu-id="8a8bd-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="8a8bd-479">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-479">String</span></span>|
|<span data-ttu-id="8a8bd-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="8a8bd-481">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-481">Int16</span></span>|
|<span data-ttu-id="8a8bd-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="8a8bd-483">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-483">Int16</span></span>|
|<span data-ttu-id="8a8bd-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="8a8bd-485">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-485">Int16</span></span>|
|<span data-ttu-id="8a8bd-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-486">REMARKS</span></span>|<span data-ttu-id="8a8bd-487">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-487">String</span></span>|
|<span data-ttu-id="8a8bd-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8a8bd-489">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="8a8bd-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8a8bd-490">ProcedureColumns</span></span>

|<span data-ttu-id="8a8bd-491">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-491">ColumnName</span></span>|<span data-ttu-id="8a8bd-492">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="8a8bd-494">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-494">String</span></span>|
|<span data-ttu-id="8a8bd-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a8bd-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="8a8bd-496">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-496">String</span></span>|
|<span data-ttu-id="8a8bd-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="8a8bd-498">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-498">String</span></span>|
|<span data-ttu-id="8a8bd-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-499">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-500">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-500">String</span></span>|
|<span data-ttu-id="8a8bd-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-501">COLUMN_TYPE</span></span>|<span data-ttu-id="8a8bd-502">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-502">Int16</span></span>|
|<span data-ttu-id="8a8bd-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-503">DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-504">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-504">Int16</span></span>|
|<span data-ttu-id="8a8bd-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-505">TYPE_NAME</span></span>|<span data-ttu-id="8a8bd-506">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-506">String</span></span>|
|<span data-ttu-id="8a8bd-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="8a8bd-507">PRECISION</span></span>|<span data-ttu-id="8a8bd-508">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-508">Int32</span></span>|
|<span data-ttu-id="8a8bd-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="8a8bd-509">LENGTH</span></span>|<span data-ttu-id="8a8bd-510">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-510">Int32</span></span>|
|<span data-ttu-id="8a8bd-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="8a8bd-511">SCALE</span></span>|<span data-ttu-id="8a8bd-512">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-512">Int16</span></span>|
|<span data-ttu-id="8a8bd-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="8a8bd-513">RADIX</span></span>|<span data-ttu-id="8a8bd-514">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-514">Int16</span></span>|
|<span data-ttu-id="8a8bd-515">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="8a8bd-515">NULLABLE</span></span>|<span data-ttu-id="8a8bd-516">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-516">Int16</span></span>|
|<span data-ttu-id="8a8bd-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-517">REMARKS</span></span>|<span data-ttu-id="8a8bd-518">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-518">String</span></span>|
|<span data-ttu-id="8a8bd-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="8a8bd-519">OVERLOAD</span></span>|<span data-ttu-id="8a8bd-520">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-520">Int32</span></span>|
|<span data-ttu-id="8a8bd-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-522">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="8a8bd-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8a8bd-523">ProcedureParameters</span></span>

|<span data-ttu-id="8a8bd-524">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="8a8bd-524">ColumnName</span></span>|<span data-ttu-id="8a8bd-525">DataType</span><span class="sxs-lookup"><span data-stu-id="8a8bd-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="8a8bd-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="8a8bd-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="8a8bd-527">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-527">String</span></span>|
|<span data-ttu-id="8a8bd-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="8a8bd-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="8a8bd-529">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-529">String</span></span>|
|<span data-ttu-id="8a8bd-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="8a8bd-531">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-531">String</span></span>|
|<span data-ttu-id="8a8bd-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-532">COLUMN_NAME</span></span>|<span data-ttu-id="8a8bd-533">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-533">String</span></span>|
|<span data-ttu-id="8a8bd-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-534">COLUMN_TYPE</span></span>|<span data-ttu-id="8a8bd-535">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-535">Int16</span></span>|
|<span data-ttu-id="8a8bd-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-536">DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-537">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-537">Int16</span></span>|
|<span data-ttu-id="8a8bd-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8a8bd-538">TYPE_NAME</span></span>|<span data-ttu-id="8a8bd-539">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-539">String</span></span>|
|<span data-ttu-id="8a8bd-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-540">COLUMN_SIZE</span></span>|<span data-ttu-id="8a8bd-541">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-541">Int32</span></span>|
|<span data-ttu-id="8a8bd-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8a8bd-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="8a8bd-543">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-543">Int32</span></span>|
|<span data-ttu-id="8a8bd-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="8a8bd-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="8a8bd-545">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-545">Int16</span></span>|
|<span data-ttu-id="8a8bd-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="8a8bd-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="8a8bd-547">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-547">Int16</span></span>|
|<span data-ttu-id="8a8bd-548">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="8a8bd-548">NULLABLE</span></span>|<span data-ttu-id="8a8bd-549">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-549">Int16</span></span>|
|<span data-ttu-id="8a8bd-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="8a8bd-550">REMARKS</span></span>|<span data-ttu-id="8a8bd-551">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-551">String</span></span>|
|<span data-ttu-id="8a8bd-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="8a8bd-552">COLUMN_DEF</span></span>|<span data-ttu-id="8a8bd-553">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-553">String</span></span>|
|<span data-ttu-id="8a8bd-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="8a8bd-555">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-555">Int16</span></span>|
|<span data-ttu-id="8a8bd-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="8a8bd-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="8a8bd-557">Int16</span><span class="sxs-lookup"><span data-stu-id="8a8bd-557">Int16</span></span>|
|<span data-ttu-id="8a8bd-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8a8bd-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="8a8bd-559">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-559">Int32</span></span>|
|<span data-ttu-id="8a8bd-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8a8bd-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="8a8bd-561">Int32</span><span class="sxs-lookup"><span data-stu-id="8a8bd-561">Int32</span></span>|
|<span data-ttu-id="8a8bd-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8a8bd-562">IS_NULLABLE</span></span>|<span data-ttu-id="8a8bd-563">String</span><span class="sxs-lookup"><span data-stu-id="8a8bd-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="8a8bd-564">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a8bd-564">See also</span></span>

- [<span data-ttu-id="8a8bd-565">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8a8bd-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
